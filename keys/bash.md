bash

```
someErrorFromCommand 2> >(xargs -I{} notify-send -u critical "Test" {}) # on error it gives notify and nothing if command succeeds 
```

