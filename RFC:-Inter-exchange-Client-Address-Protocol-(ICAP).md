### Forward

Transferring funds between third-party accounts, especially those of exchanges, places considerable burden on the user and is error prone, due to the way in which deposits are identified to the client account. This problem was tackled by the existing banking industry through having a common code known as *IBAN*. This code amalgamated the institution and client account along with a error-detection mechanism practically eliminating trivial errors and providing considerable convenience for the user. Unfortunately, this is a heavily regulated and centralised service accessible only to large, well-established institutions. This protocol may be viewed is a decentralised version of it suitable for any institutions containing funds on the Ethereum system.

### IBAN

For a good overview of the IBAN system, please see [Wikipedia's IBAN article](https://en.wikipedia.org/wiki/International_Bank_Account_Number). An IBAN code consists of up to 34 case insensitive alpha-numeric characters. It contains three pieces of information:

- The country code; a top-level identifier for the context of the following (ISO 3166-1 alpha-2);
- The error-detection code; uses the *mod-97-10* checksumming protocol (ISO/IEC 7064:2003);
- The basic bank account number (BBAN); an identifier of the institution, branch and client account, whose composition is dependent on the aforementioned country.

For the UK, the BBAN is composed of:

- Institution identifier, 4-character alphabetical, e.g. `MIDL` (ironically) represents HSBC bank.
- Sort-code (branch identifier within the institution), a 6-digit decimal number, e.g. `402702` would be the Lancaster branch of HSBC.
- Account number (client identifier within the branch), an 8-digit decimal number.

# Proposed Design

Introduce a new IBAN country code: *XE*, formulated as the Ethereum *E* prefixed with the "extended" *X*, as used in non-jurisdictional currencies (e.g. XRP, XCP).

The BBAN for this code will comprise three fields:

- Asset identifier, 3-character alphanumeric (< 16-bit);
- Institution identifier, 4-character alphanumeric (< 21-bit);
- Institution client identifier, 9-character alphanumeric (< 47-bit);

Including the four initial characters, this leads to a final client-account address length of 20 characters, of the form:

```
XE66ETHXREGGAVOFYORK
```

Split into:

- `XE` The country code for Ethereum;
- `66` The checksum;
- `ETH` The asset identifier within the client account - in this case, "ETH" is the only valid asset identifier, since Ethereum's base registry contract supports only this asset;
- `XREG` The institution code for the account - in this case, Ethereum's base registry contract;
- `GAVOFYORK` The client identifier within the institution - in this case, a direct payment with no additional data to whatever primary address is associated with the name "GAVOFYORK" in Ethereum's base registry contract;

### Notes

Institution codes beginning with `X` are reserved for system use.

## Implementation

The mechanism for asset transfer over two routing protocols are specified, both of which are specific to the Ethereum domain (country-code of `XE`). One is for currency transfers directly to clients with the system address found through a Registry-lookup system of the client-ID, denoted by asset class `ETH`, whereas the other is for transfers to an intermediary with associated data to specify client, denoted by asset class `XET`.

### ETH

Within the ETH asset code of Ethereum's country-code (XE), i.e. as long as the code begins with `XE**ETH` (where `**` is the valid checksum), then we can define the required transaction to be the deposit address given by a call to the *registry contract* denoted by the institution code. For institutions not beginning with `X`, this corresponds to the primary address associated with the *Ethereum standard name*:

[institution code] `/` [client identifier]

The *Ethereum standard name* is simply the normal hierarchical lookup mechanism, as specified in the Ethereum standard interfaces document.

We define a *registry contract* as a contract fulfilling the Registry interface as specified in the Ethereum standard interfaces document.

**TODO**: JS code for specifying the transfer.

### XET

For the `XET` asset code within the Ethereum country code (i.e. while the code begins XE**XET), then we can derive the transaction that must be made through a lookup to the Ethereum `iban` registry contract. For a given institution, this contract specifies two values: the deposit call signature hash and the institution's Ethereum address.

At present, only a single such deposit call is defined, which is:

```
function deposit(uint64 clientAccount)
```

whose signature hash is `0x13765838`. The transaction to transfer the assets should be formed as an ether-laden call to the institution's Ethereum address using the `deposit` method as specified above, with the client account determined through the value of the big-endian, base-36 interpretation of the alpha-numeric *Institution client identifier*, literally using the value of the characters `0` to `9`, then evaluating 'A' (or 'a') as 10, 'B' (or 'b') as 11 and so forth.

**TODO**: JS code for specifying the transfer.

## Other forms

### URI

General URIs can be formed though the URI scheme name `iban`, followed by the colon character `:`, followed by the 20-character alphanumeric identifier, thus for the example above, we would use:

```
iban:XE66ETHXREGGAVOFYORK
```

### QR Code

A QR code may be generated directly from the URI using standard QR encodings. For example, the example above `iban:XE66ETHXREGGAVOFYORK` would have the corresponding QR code:

![QR code for iban:XE66ETHXREGGAVOFYORK](http://opensecrecy.com/qr-XE66ETHXREGGAVOFYORK.gif)