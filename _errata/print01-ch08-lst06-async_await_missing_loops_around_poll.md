---
chapter: 8
kind: code
reporter: ilya-epifanov
page: 125
date: 2022-01-09
# fixed: 2021-01-01
---
Listing 8-6 says

```rust
generator fn forward<T>(rx: Receiver<T>, tx: Sender<T>) {
    loop {
        let mut f = rx.next();
        let r = if let Poll::Ready(r) = f.poll() {
            r
        } else {
            yield
        };
        if let Some(t) = r {
            let mut f = tx.send(t);
            let _ = if let Poll::Ready(r) = f.poll() {
                r
            } else {
                yield
            };
        } else {
            break Poll::Ready(());
        }
    }
}
```

but should say

```rust
generator fn forward<T>(rx: Receiver<T>, tx: Sender<T>) {
    loop {
        let mut f = rx.next();
        let r = loop {
            if let Poll::Ready(r) = f.poll() {
                break r
            } else {
                yield
            }
        };
        if let Some(t) = r {
            let mut f = tx.send(t);
            let _ = loop {
                if let Poll::Ready(r) = f.poll() {
                    break r
                } else {
                    yield
                }
            };
        } else {
            break Poll::Ready(());
        }
    }
}
```
