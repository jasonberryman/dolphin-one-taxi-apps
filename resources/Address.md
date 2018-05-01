# Resource: Address

An address document

## JSON representation

```json
{
  "addressId": String,
  "organization": String,
  "building": String, // The building name or number
  "street": String,
  "city": String,
  "region": STring,
  "postCode": STring,
  "formatted": String, // The adress to be read by the IVR.  If this is omitted, the IVR will use the building and street
  "phonetic": String, // A phonetic version of the address for difficult to pronounce names
  "zoneId": String,
  "zoneName": String,
  "delayMinutes": Integer,
  "type": String, // The type of address: hotel, restaurant, airport, etc.
  "tags": Array
}
```


## Fields

| Fields | Description | Example |
| :---: | --- | :---: |
| addressId | **String**<br><br>A unique ID for this address.  This is used to notify the dispatch system when a caller makes a new booking request.<br><br>Required. | 76458912 |
| organization | **String**<br><br>The name of an organization.<br><br>Optional. | McDonald's Restaurants Ltd. |
| building | **String**<br><br>The building name or number.<br><br>Optional. | 41 |
| street | **String**<br><br>The street name<br><br>Optional. | Winchester Circle |
| city | **String**<br><br>The town or city<br><br>Optional. | Milton Keynes |
| region | **String**<br><br>The county, state or region where the town or city is located<br><br>Optional. | Buckinghamshire |
| postCode | **String**<br><br>The post code or zip code.<br><br>Optional. | MK10 0BA |
| formatted | **String**<br><br>The formatted address<br><br>Optional. | McDonald’s Restaurants Ltd, 41 Winchester Circle, Kingston |
| phonetic | **String**<br><br>The name to be read out by the IVR<br><br>Optional. | McDonald's Kingston |
| zoneId | **String**<br><br>The ID for the zone where this address is located.<br><br>Optional. | KNG |
| zoneName | **String**<br><br>The name of the zone<br><br>Optional. | Kingston |
| delayMinutes | **Integer**The number of minutes delay for any pickup from this address.<br><br>Optional. | 15 |
| type | **String**<br><br>The type of location.<br><br>Optional. | restaurant |
| tags | **Array**<br><br>A list of tags that could be assiciated with this address.<br><br>Optional. | fastFood, restaurant |
