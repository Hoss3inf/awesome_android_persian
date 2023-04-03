# awesome_android_persian
A collection of Persian Android Libraries

## Shamsi Calenadars (solar calendars)
### 1. [persianDate By SamanZamani](https://github.com/samanzamani/PersianDate)


example:
```
PersianDate pdate = new PersianDate();
PersianDateFormat pdformater1 = new PersianDateFormat('Y/m/d');
pdformater1.format(pdate);//1396/05/20

PersianDateFormat pdformater2 = new PersianDateFormat('y F j');
pdformater2.format(pdate);//۱۹ تیر ۹۶
```

### 2. [persian date-time](https://github.com/mfathi91/persian-date-time)
substitute for `DateTime` library in java. usage example:

```
// Instantiate 
PersianDate today = PersianDate.now();
PersianDate persianDate1 = PersianDate.of(1396, 7, 15);
PersianDate persianDate2 = PersianDate.of(1396, PersianMonth.MEHR, 15);

// Convert
PersianDate persianDate5 = PersianDate.of(1397, 5, 11);
LocalDate gregDate = persianDate.toGregorian();    // => '2018-08-02'
PersianDate persianDate6 = PersianDate.fromGregorian(gregDate);  //  => '1397/05/11'

// Parse
PersianDate persianDate3 = PersianDate.parse("1400-06-15");    // From the standard format
PersianDate persianDate4 = PersianDate.parse("1400/06/15", DateTimeFormatter.ofPattern("yyyy/MM/dd"));    // From a desired format

// Format
DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy/MM/dd");
dtf.format(PersianDate.now());    // => e.g. '1396/05/10'
```

## Shamsi DatePickers (solar date Pickers)
### 1. [Persian-date-picker-dialog](https://github.com/aliab/Persian-Date-Picker-Dialog)
[logo]: [https://raw.githubusercontent.com/aliab/Persian-Date-Picker-Dialog/master/screenshot/heroimage.jpg](https://raw.githubusercontent.com/aliab/Persian-Date-Picker-Dialog/master/screenshot/heroimage.jpg) "Logo Title Text 2"

