# JavaScript exchange API wrapper ([Changenow.io](https://changenow.io/))


## API Key

To access the ChangeNOW API you need to generate an API key. You can get one in [your personal affiliate account](https://changenow.io/affiliate) or by emailing us at [api@changenow.io](mailto:api@changenow.io).


## Exchange flow
All API methods wrapped by only the one function ```cnApiWrapper```. Which has three parameters ```callName```, ```callPrams```, ```callback```.<br/><br/>
```callName``` - one of the API calls, which you want to request.<br/>
```callPrams``` - this is an javaScript object, if the ```callName``` has required parameter, you need to pass it here. 
```callback``` - (optional) this is a function that is called after the request is completed, an API response is passed to it.

## How to use

Add a script link to your HTML before your main script
```html
<body>
  <script src="changenowApi/changenowApi.js"></script>
  <script src="your-script.js"></script>
</body>  
```
Use ```cnApiWrapper``` function to interact with all available actions in API.  
example:
```js
  const response = await cnApiWrapper('CURRENCIES', { fixedRate: true });
  console.log(response);
```
or use callback:  
```js
  const callback = (response) => { console.log(response) };
  cnApiWrapper('CURRENCIES', { fixedRate: true }, callback);
```


### Supported calls and parameters
Expected result | Calls and parameters
------------- | -------------
*List of all available currencies.* | *callName* - CURRENCIES<br/>*callParameters:*<br/>**isActive** - (Optional) Set true to return only active currencies (It's used for Standart flow). <br/>**fixedRate** - (Optional) Set true to return only for the currencies available on a fixed-rate flow
*List of available currencies for a specific currency.* | *callName* - CURRENCIES_TO<br/>*callParameters:*<br/>**ticker** - (Required) Currency ticker.<br/>**fixedRate** - (Optional) Set true to return only for the currencies available on a fixed-rate flow
*Currency info* | *callName* - CURRENCY_INFO<br/>*callParameters:*<br/>**ticker** - (Required) Currency ticker.
*List of transactions* | *callName* - LIST_OF_TRANSACTIONS<br/>*callParameters:*<br/>**apiKey** - (Required) Partner public API key<br/>**tickerFrom** - (Optional) Set a ticker of a payin currency to filter transactions<br/>**tickerTo** - (Optional) Set a ticker of a payout currency to filter transactions<br/>**status** - (Optional) Set a transaction status (available statuses below) to filter transactions<br/>**limit** - (Optional) Limit of transactions to return (default: 10)<br/>**offset** - (Optional) Number of transactions to skip (default: 0)<br/>
*Transaction status* | *callName* - TX_STATUS<br/>*callParameters:*<br/>**id** - Transaction ID from Create transaction request<br/>**apiKey** - (Required) Partner public API key
*Estimated exchange amount* | *callName* - ESTIMATED<br/>*callParameters:*<br/>**amount** - Amount of funds you want to exchange. <br/>**from** - Ticker of the currency you want to send<br/>**to** - Ticker of the currency you want to receive<br/>**apiKey** - (Required) Partner public API key<br/>**fixedRate** - (Optional) Set true to return only for the currencies available on a fixed-rate flow
*Create exchange transaction* | *callName* - CREATE_TX<br/>*callParameters:*<br/>**apiKey** - (Required) Partner public API key.<br/>**from** - (Required) Ticker of a currency you want to send.<br/>**to** - (Required) Ticker of a currency you want to receive.<br/>**address** - (Required) Address to receive a currency.<br/>**amount** - (Required) Amount you want to exchange.<br/>**extraId** - (Optional) Extra ID for currencies that require it.<br/>**refundAddress** - (Optional) Refund address.<br/>**refundExtraId** - (Optional) Refund Extra ID.<br/>**userId** - (Optional) Partner user ID.<br/>**payload** - (Optional) Object that can contain up to 5 arbitrary fields up to 64 characters long.<br/>**contactEmail** - (Optional) Your contact email for notification in case something goes wrong with your exchange<br/>**fixedRate** - (Optional) Set true to return only for the currencies available on a fixed-rate flow
 *List of all available pairs* | *callName* - PAIRS<br/>*callParameters:*<br/>**includePartners** - Set false to return all available pairs, except pairs supported by our partners.<br/>
  *List of all available fixed rate pairs* | *callName* - FIXED_RATE_PAIRS<br/>*callParameters:*<br/>**apiKey** - (Required) Partner public API key<br/>
 *Minimal exchange amount* | *callName* - MIN_AMOUNT<br/>*callParameters:*<br/>**from** - Ticker of the currency you want to send.<br/>**to** - Ticker of the currency you want to receive.

### Full version of API documentation
All methods described here ([API Documentation](https://changenow.io/api/docs)).

## Any questions
If you would like to contribute code you can do so through GitHub by forking the repository and sending a pull request.

If you have any question create an issue.

## License
Library are licensed under the [GPL-3.0 License](LICENSE).

Enjoy!
