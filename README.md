# Slack Hooks for zap

## Example

``` go
package main

import (
	"github.com/bluele/zapslack"
	"go.uber.org/zap"
)

func main() {
    // Please rewrite it with your webhook URL
	slackWebHookURL := "https://hooks.slack.com/services/XXXXX/YYYYY/ZZZZZ"

	logger, _ := zap.NewProduction()

	// Send a notification to slack at only error, fatal, panic level
	logger = logger.WithOptions(
		zap.Hooks(zapslack.NewSlackHook(slackWebHookURL, zap.ErrorLevel).GetHook()),
	)

	logger.Debug("don't need to send a message")
	logger.Error("an error happened!")
}
```

## Install

```
$ go get -u github.com/bluele/zapslack
```

## Author

**Jun Kimura**

* <http://github.com/bluele>
* <junkxdev@gmail.com>
