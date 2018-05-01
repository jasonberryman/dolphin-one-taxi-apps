# Resource: InviteSnapshot

An invite document

## JSON representation

```json
{
  "customerId": String,
  "name": String,
  "driverRef": String,
  "priority": String,
  "pickups": [
    { Object(Address) }
  ],
  "destinations": [
    { Object(Address) }
  ],
  "bookings": [
    { Object(Booking) }
  ],
  "phones": [
    { Object(Phone) }
  ],
  "tags": [
    String
  ]
}
```


## Fields

| Fields | Description | Example |
| :---: | --- | :---: |
| customerId or driverId | **String**<br><br>The unique ID of the caller, as defined in the booking system.  This will allow us to create bookings and relate them to this customer.<br><br>Required. | 4675891 |
| name | **String**<br><br>The name of the caller (customer / driver) | John Smith |
| driverRef | **String**<br><br>If this is a driver, you can specify the driver reference used by the taxi company.<br><br>Optional. | 243 |
| priority | **String**<br><br>The priority level for this caller to be connected to an agent<br><br>**Accepted values:**<br><br>* low<br>* normal<br>* high<br>* urgent<br><br>Optional. | normal |
| pickups | **Array**<br><br>An array of [Address](Address.md) resources showing which addresses the customer can be offered by an automated service, such as IVR.  We normally recommend that you restrict this to no more than 3 addresses and should be configurable by the company (in your app).  Typically, an app will give us the top 3 addresses which have been used more than `n` times in `x` days, where at least one of those times has been within the last 7 days.<br><br>If these addresses can be tagged with a shortname, such as "home" or "work" or "station", this can improve the booking experience.<br><br>Optional. | |
| destinations | **Array**<br><br>An array of [Address](Address.md) resources offering the customer a destination, when they make an automated booking.  These addresses should be relevant to the customer and related to the pickup address.<br><br>For example, if the customer is being picked up from home, possible destinations may be "work" or "station" and could be related to the time of day.<br><br>Optional.  This is not required for IVR to take bookings.<br><br>Optional. | |
| bookings | **Array**<br><br>An array of [Booking](Booking.md) resources, listing any existing bookings in the system, which have not yet cleared.  This information is provided to allow customers to amend / delete bookings or connect with the driver (`enroute` / `arrived` status only).<br><br>This data is also provided for calls from drivers (`?queueType=driver`), so that they can be connected to the customer (`enroute` / `arrived` status only).<br><br>Optional. | |
| phones | **Array**<br><br>An array of [Phone](Phone.md) resources, listing the phone numbers attached to this caller. | |
| tags | **Array**<br><br>An array of tags to allow us to process any bookings in a particular way.<br><br>**Allowable values:**<br><br>* noIVR (the caller will _always_ be connected directly to an agent)<br>* fixed (only one pickup address should be sent)<br>* asapOnly (no pre-booking allowed)<br>* hotel (Room number is requested)<br>* restaurant (Table number is requested)<br><br>If any of these tags are set, **no** existing booking data is required / read to the caller and the caller will **not** have the option to connect with the driver.<br><br>If `hotel` and `restaurant` are added, the IVR will ask them to confirm if they are entering a room or table number.<br><br>Optional. | |
