go-yobit
========
go-yobit is an implementation of the Yobit exchange API in Golang.

##Supports  
* Public API
* Trade API
* Cloudflare challenge solver

##Import
~~~go
import "github.com/ikonovalov/go-yobit"
~~~

##Usage
~~~go
package main
import "github.com/ikonovalov/go-yobit"

credential := yobit.ApiCredential{Key: 'zzz', Secret: 'ggg'}
yo := yobit.New(credential)
defer yo.Release()

// get tickers
tickersChan := make(chan yobit.TickerInfoResponse)
go yo.Tickers24(usdPairs, tickersChan)
tickerRs := <-tickersChan

// get wallet balances
channel := make(chan yobit.GetInfoResponse)
go yo.GetInfo(channel)
getInfoRes := <-channel
~~~

[MIT License](LICENSE)