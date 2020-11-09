# mediawiki-GoogleRichCards
MediaWiki extension to generate Google Rich Cards metadata for article pages

mediawiki.org extension page: https://www.mediawiki.org/wiki/Extension:GoogleRichCards

# Features
The extension adds Google Rich Card JSON-LD metadata to each "content page" of your MediaWiki installation.
Currently it supports the following types:

 * Article (status: stable)
 * WebSite (status: beta)
 * Event (status: alpha)

# Installation

### Download code
```
git clone https://github.com/teran/mediawiki-GoogleRichCards.git <mediawiki path>/extensions/GoogleRichCards
```

### LocalSettings.php
```
// Load extension
wfLoadExtension('GoogleRichCards');

// Enable annotations for articles
$wgGoogleRichCardsAnnotateArticles = true;

// Enable annotations for events
$wgGoogleRichCardsAnnotateEvents = true;

// Enable WebSite annotations
$wgGoogleRichCardsAnnotateWebSite = true;
```

### Template:Event
```
<event 
name="{{{name}}}" 
startDate="{{{startDate}}}" 
endDate="{{{endDate}}}"
description="{{{description}}}"
image="{{{image}}}"
attendancemode="{{{attendancemode}}}" 
eventstatus="{{{eventstatus}}}"
virtualvendorurl="{{{virtualvendorurl}}}"
place="{{{place}}}"
streetaddress="{{{streetAddress}}}" 
postalCode="{{{postalCode}}}" 
locality="{{{locality}}}" 
region="{{{region}}}" 
country="{{{country}}}" 
offer="{{{offer}}}" 
offerURL="{{{offerURL}}}" 
offerPrice="{{{offerPrice}}}" 
offerCurrency="{{{offerCurrency}}}" 
offerAvailability="{{{offerAvailability}}}" 
validFrom="{{{validFrom}}}"
performer="{{{performer}}}"
performer_url="{{{performer_url}}}" 
performer_sameAs="{{{performer_sameas}}}"
contributor="{{{contributor}}}" 
contributor_url="{{{contributor_url}}}" 
contributor_sameas= "{{{contributor_sameas}}}" 
contributor_name="{{{contributor_name}}}" 
contributor_award="{{{contributor_award}}}" 
organizer="{{{organizer}}}"
organizer_url="{{{organizer_url}}}"
/>

```

Please note, you're free to update this template in order to setup events publishing in your own flavour

### Usage of Event template

```
{{Event
|name=Track day
|startDate=2018-06-01T10:00+03:00
|endDate=2018-06-01T20:00+03:00
|description=First track day in June
|image=https://example.com/trackday.jpg
|attendancemode=    <!--MixedEventAttendanceMode OfflineEventAttendanceMode OnlineEventAttendanceMode-->
|eventstatus=       <!--EventCancelled EventMovedOnline EventPostponed EventRescheduled EventScheduled-->
|virtualvendorurl=  https://example.com/ticketVendorOnlineshow

|place=Moscow Raceway
|streetAddress=95th km of Novorizhskoe highway (М9)
|postalCode=000000
|locality=Moscow district
|region=District of Volokolamsk
|country=RU

|offer =  {{#var: event_name |none}}
|offerPrice=5
|offerCurrency= USD
|offerAvailability=       <!-- Discontinued InStock InStoreOnly LimitedAvailability OnlineOnly OutOfStock PreOrder PreSale SoldOut -->
|offerURL=http://example.com/test-event
|validFrom=2018-06-01T10:00+03:00

|performer=awesome performer
|performer_url=https://example.com/awesomePerformerHomepage/
|performer_sameas=https://example.com/awesomePerformerHomepage/Wiki

|contributor=another performer
|contributor_url= https://example.com/anotherPerformerHomepage/
|contributor_sameas=https://example.com/anotherPerformerHomepage/Wiki
|contributor_award=https://example.com/anotherPerformerHomepage/Award

|organizer= organizer name
|organizer_url=https://example.com/organizersPage
}}


```
