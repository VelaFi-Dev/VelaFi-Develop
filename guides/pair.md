---
icon: bagel
metaLinks:
  alternates:
    - https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/guides/pair
---

# Pair

This section provides information about the various trading pairs supported by the API, including on/off ramp and global payment pairs.

### **On/Off Ramp Pair**

The following are some of the listed currency pairs. The complete list of currency pairs can be obtained through the following interface: [Fiat/Crypto](../api-reference/basic-configuration/get-fiat-crypto-pairs.md) or [Crypto/Fiat](../api-reference/basic-configuration/get-crypto-fiat-pairs.md)  Pairs.

<table><thead><tr><th width="174">Country</th><th width="97">Fiat</th><th>Crypto</th><th width="103">Decimals</th><th>On-Ramp</th><th>Off-Ramp</th></tr></thead><tbody><tr><td>🇦🇷 Argentina</td><td>ARS</td><td>BTC</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇦🇷 Argentina</td><td>ARS</td><td>USDC</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇦🇷 Argentina</td><td>ARS</td><td>USDT</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇧🇷 Brazil</td><td>BRL</td><td>USDC</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇧🇷 Brazil</td><td>BRL</td><td>USDT</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇨🇴 Colombia</td><td>COP</td><td>USDC</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇨🇴 Colombia</td><td>COP</td><td>USDT</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇭🇰 Hong Kong</td><td>USD</td><td>MMXN</td><td>4</td><td>No</td><td>Yes</td></tr><tr><td>🇭🇰 Hong Kong</td><td>USD</td><td>USDC</td><td>4</td><td>No</td><td>Yes</td></tr><tr><td>🇭🇰 Hong Kong</td><td>USD</td><td>USDT</td><td>4</td><td>No</td><td>Yes</td></tr><tr><td>🇲🇽 Mexico</td><td>MXN</td><td>BTC</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇲🇽 Mexico</td><td>MXN</td><td>MMXN</td><td>2</td><td>Yes</td><td>Yes</td></tr><tr><td>🇲🇽 Mexico</td><td>MXN</td><td>USDC</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇲🇽 Mexico</td><td>MXN</td><td>USDT</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇵🇪 Peru</td><td>PEN</td><td>USDT</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇵🇪 Peru</td><td>USD</td><td>USDT</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇺🇸 United States</td><td>EUR</td><td>USDC</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇺🇸 United States</td><td>EUR</td><td>USDT</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇺🇸 United States</td><td>USD</td><td>USDC</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>🇺🇸 United States</td><td>USD</td><td>USDT</td><td>4</td><td>Yes</td><td>Yes</td></tr><tr><td>gl Global</td><td>USD</td><td>USDC</td><td>4</td><td>No</td><td>Yes</td></tr><tr><td>gl Global</td><td>USD</td><td>USDT</td><td>4</td><td>No</td><td>Yes</td></tr></tbody></table>

### **Global Payment Pair**

The following are some of the listed currency pairs. The complete list of currency pairs can be obtained through the following interface: [Fiat/Fiat](pair.md#global-payment-pair) Pairs.

<table><thead><tr><th width="167">Sending country</th><th width="109">Sending currency</th><th>Receiving country</th><th>Receiving currency</th><th>Decimals</th></tr></thead><tbody><tr><td>🇦🇷 Argentina</td><td>ARS</td><td>🇲🇽 Mexico</td><td>MXN</td><td>4</td></tr><tr><td>🇦🇷 Argentina</td><td>ARS</td><td>🇺🇸 United States</td><td>USD</td><td>8</td></tr><tr><td>🇧🇷 Brazil</td><td>BRL</td><td>🇦🇷 Argentina</td><td>ARS</td><td>4</td></tr><tr><td>🇧🇷 Brazil</td><td>BRL</td><td>🇭🇰 Hong Kong</td><td>USD</td><td>4</td></tr><tr><td>🇧🇷 Brazil</td><td>BRL</td><td>gl Global</td><td>USD</td><td>4</td></tr><tr><td>🇨🇴 Colombia</td><td>COP</td><td>🇲🇽 Mexico</td><td>MXN</td><td>2</td></tr><tr><td>🇲🇽 Mexico</td><td>MXN</td><td>🇦🇷 Argentina</td><td>ARS</td><td>4</td></tr><tr><td>🇲🇽 Mexico</td><td>MXN</td><td>🇨🇴 Colombia</td><td>COP</td><td>2</td></tr><tr><td>🇲🇽 Mexico</td><td>MXN</td><td>🇭🇰 Hong Kong</td><td>USD</td><td>4</td></tr><tr><td>🇲🇽 Mexico</td><td>MXN</td><td>🇺🇸 United States</td><td>USD</td><td>4</td></tr><tr><td>🇲🇽 Mexico</td><td>MXN</td><td>gl Global</td><td>USD</td><td>4</td></tr><tr><td>🇺🇸 United States</td><td>USD</td><td>🇦🇷 Argentina</td><td>ARS</td><td>4</td></tr><tr><td>🇺🇸 United States</td><td>USD</td><td>🇲🇽 Mexico</td><td>MXN</td><td>2</td></tr></tbody></table>
