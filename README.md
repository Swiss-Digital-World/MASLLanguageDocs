# MASL (Marine Survey Language)

## Introduction

MASL is a preprocessor scripting language designed to enpower the tools within the Marine Survey App through custom expressions along with markdown editor in which you can use markdown along with MASL expressions to design any format for your report template

## Getting started

You can get started by going in the `reporting section` of any survey that you created and then in the custom template options you would see a our MASL Editor on which you can script your template format 

## Page components

MASL provides support for header and footer along with other parts of the report of which some are specific to the marine survey report and others are general purpose to other languages we provide 

> **Header**

```MASL
@beginheader
  Text In Header
@endheader
```

In the above example a header is created with the word 'Text In Header' in the left side of the header

> **Footer**

```MASL
@beginfooter
  @pagenumber
@endfooter
```

In the above example a footer is created with the page number for each page automatically generated for new pages


## Cover Page

> Basic Example

```MASL
@begincoverpage

@beginheader
Cover Page Header
@endheader

@endcoverpage
```

In the above example a cover page is added to the report with the header that has the word 'Cover Page Header' which is only available for the cover page and then other pages can have another header you can specify as in the header section

## Grid System

Grid system means that you can place items as grids basically rows and columns so that you can place items to the right and left of your report space

###### Example 1 (Row with dynamic number of columns)
```MASL
@beginrow

@begincol
  Column
@endcol

@begincol
  Column
@endcol

@begincol
  Column
@endcol

@begincol
  Column
@endcol

@begincol
  Column
@endcol

@begincol
  Column
@endcol

@begincol
  Column
@endcol

@begincol
  Column
@endcol

@begincol
  Column
@endcol

@endrow
```

###### Example 2 (Row with 2 columns)
```MASL
@beginrow2

@begincol2
  Column
@endcol2

@begincol2
  Column
@endcol2

@endrow2
```

###### Example 3 (Row with 3 columns)
```MASL
@beginrow3

@begincol3
  Column
@endcol3

@begincol3
  Column
@endcol3

@begincol3
  Column
@endcol3

@endrow3
```

###### Example 4 (Row with 4 columns)
```MASL
@beginrow4

@begincol4
  Column
@endcol4

@begincol4
  Column
@endcol4

@begincol4
  Column
@endcol4

@begincol4
  Column
@endcol4

@endrow4
```

###### Example 5 (Row with 5 columns)
```MASL
@beginrow5

@begincol5
  Column
@endcol5

@begincol5
  Column
@endcol5

@begincol5
  Column
@endcol5

@begincol5
  Column
@endcol5

@begincol5
  Column
@endcol5

@endrow5
```

###### Example 6 (Row with 6 columns)
```MASL
@beginrow6

@begincol6
  Column
@endcol6

@begincol6
  Column
@endcol6

@begincol6
  Column
@endcol6

@begincol6
  Column
@endcol6

@begincol6
  Column
@endcol6

@begincol6
  Column
@endcol6

@endrow6
```

## Survey Data

You can access the survey data using the directive @survey as below

```MASL
@survey('name') // Gives the name of the survey
@survey('dateAdded') // Gives the date at which the survey was created
@survey('fullName') // Gives the client for the survey
@survey('referenceNumber') // Gives the reference number for the survey
@survey('startdate') // Gives the start date of the survey
@survey('enddate') // Gives the end date of the survey

// etc
```

## Port Data

```MASL
@beginportdata

Port Data

@port('name')
@port('number')
@port('berth')

Port Data Photo Notes

@beginfornote
@note('note')
@note('date')
@note('time')
@noteimg('100x100')
@endfornote

@endportdata
```

## Vessel Data

```MASL
@beginvesseldata

Vessel Data

### @vessel('name')
### Manager: @vessel('manager')

IMO: @vessel('imo')

Length: @vessel('length') meters
Draft: @vessel('draft') meters
GT: @vessel('gt') tons
NT: @vessel('nt') tons
DWT: @vessel('dwt') tons

Vessel Data Photo Notes

@beginfornote
Note: @note('note')
Date: @note('date') @note('time')
@noteimg('100x100')
@newline
@endfornote

Vessel Data Holds

@beginforhold
#### @hold('notes') at @hold('date')
Dimensions: @hold('l') x @hold('w') x @hold('h')
@endforhold

@endvesseldata
```

## Cargo Data

```MASL
@begincargodata

Cargo Data

Total Freight Tons: @cargo('total_freight_tons')
Total Packages: @cargo('packages')
Total Weight: @cargo('weight')

Cargo Data Photo Notes

@beginfornote
Note: @note('note')
Date: @note('date') at @note('time')
@noteimg('100x100')
@endfornote

Cargo Data Packages

@beginforpackage

Package Data

Number: @package('number')
Date: @package('date')
Description: @package('description')

Package Photo Notes

@beginfornote
Note: @note('note')
Date: @note('date') at @note('time')
@noteimg('50x50')
@endfornote
@horizontalline
@endforpackage

@endcargodata
```


## User Data

You can access the current user data using the directive @user as below

```MASL
@user('username') // Gives the username of the current user
@user('email') // Gives the email of the current user
@user('phone') // Gives the phone of the current user
@user('address') // Gives the address of the current user (City, Country)
@user('logo,25x25') // Displays user photo in 25 pixels width by 25 pixels height (From the user details page in the settings)
@user('companylogo,30x35') // Displays user company photo in 30 pixels width by 35 pixels height (From the user details page in the settings)

// etc
```

## Client Data

You can access the current user data using the directive @client as below

```MASL
@client('name') // Gives the name of the survey client
@client('phone') // Gives the phone number of the survey client
@client('email') // Gives the email of the survey client
@client('company') // Gives the compnay name of the survey client
@client('address') // Gives the address of the survey client (City, Country)
@client('logo,30x35') // Displays client company photo in 30 pixels width by 35 pixels height

// etc
```

## Events 

you can manage events data in multiple ways and forms and here are some examples 

Example 1:

The below code generates the word Event Content for the number of events the survey has

```MASL
@beginforevent

Event Content

@endforevent
```

Example 2: 

The below code generates the name of the event in the loop

```MASL
@beginforevent

@event('name')

@endforevent
```

Example 3: 

The below code generates the name of the event in the loop and then loop through the notes in the event to display photos and notes

Warning: Please note that @beginfornote is not to be used outside of the @beginforevent block 

```MASL
@beginforevent

@event('name')

@beginfornote

@beginrow

@begincol
@note('note') // Gives the note content
@endcol

@begincol
@noteimg('100x100') // Gives the note image with height and width of 100px
@endcol

@begincol
@noteimg('fit') // Fits to width 
@endcol

@endrow

@endfornote

@endforevent
```

## Formatters

Formatters are keywords used to help facilitate page formatting like newline and horizontal lines 

| Formatter | Description |
| - | - |
| @newline | Leaves a blank line and starts a new empty line |
| @horizontalline | Generaes a horizontal separator line to separate content |
| @pagebreak | Jumps to a new empty page |
| @date | Gets the current date |
| @datetime | Gets the current date and time |
| @time | Gets the current time |


