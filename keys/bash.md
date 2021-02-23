bash

```
someErrorFromCommand 2> >(xargs -I{} notify-send -u critical "Test" {}) # on error it gives notify and nothing if command succeeds 

set -eu # should be default in script

set -e # as soon as single command fails, script fails
set -u # when undefined variable is used script breaks

set -o pipefail # specific to bash

hasflag() {
	local flag=${1} # mandatory variable, script with flags will fail
	local flag2=${1:-} # optional variable
}

```

