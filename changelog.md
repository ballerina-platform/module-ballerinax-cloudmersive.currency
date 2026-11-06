# Changelog

All notable changes to this project are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- An optional `headers` parameter on every remote method, for sending extra request headers.
- New `ConnectionConfig` fields, taken from `http:ClientConfiguration`: `followRedirects`, `cookieConfig`, `socketConfig` and `laxDataBinding`.

### Changed

- **Breaking:** the remote methods are renamed:
  - `currencyExchangeGetAvailableCurrencies` is now `listAvailableCurrencies`.
  - `currencyExchangeConvertCurrency` is now `convertCurrency`.
  - `currencyExchangeGetExchangeRate` is now `getExchangeRate`.
- **Breaking:** record fields use camel case, mapped to the API's Pascal-case JSON names with `@jsondata:Name`. For example, `ExchangeRateResult.ExchangeRate` is now `exchangeRate`, `AvailableCurrencyResponse.Currencies` is now `currencies`, and `ConvertedCurrencyResult.ISOCurrencyCode` is now `iSOCurrencyCode`.
- **Breaking:** the default `serviceUrl` is `https://api.cloudmersive.com/currency/exchange-rates`, Cloudmersive's production endpoint (was the test endpoint `https://testapi.cloudmersive.com/`). A custom `serviceUrl` must now include the `/currency/exchange-rates` path.
- **Breaking:** `ConnectionConfig.http1Settings` is now `http:ClientHttp1Settings` (was the connector's own `ClientHttp1Settings`).
- `ConnectionConfig.timeout` defaults to 30 seconds (was 60).

### Removed

- **Breaking:** the connector's own `ClientHttp1Settings` and `ProxyConfig` records. Use `http:ClientHttp1Settings` and `http:ProxyConfig` instead.
