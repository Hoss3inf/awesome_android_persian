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

example:

```
picker = new PersianDatePickerDialog(this)
                .setPositiveButtonString("باشه")
                .setNegativeButton("بیخیال")
                .setTodayButton("امروز")
                .setTodayButtonVisible(true)
                .setMinYear(1300)
                .setMaxYear(PersianDatePickerDialog.THIS_YEAR)
                .setMaxMonth(PersianDatePickerDialog.THIS_MONTH)
                .setMaxDay(PersianDatePickerDialog.THIS_DAY)
                .setInitDate(1370, 3, 13)
                .setActionTextColor(Color.GRAY)
                .setTypeFace(typeface)
                .setTitleType(PersianDatePickerDialog.WEEKDAY_DAY_MONTH_YEAR)
                .setShowInBottomSheet(true)
                .setListener(new PersianPickerListener() {
                    @Override
                    public void onDateSelected(@NotNull PersianPickerDate persianPickerDate) {
                        Log.d(TAG, "onDateSelected: " + persianPickerDate.getTimestamp());//675930448000
                        Log.d(TAG, "onDateSelected: " + persianPickerDate.getGregorianDate());//Mon Jun 03 10:57:28 GMT+04:30 1991
                        Log.d(TAG, "onDateSelected: " + persianPickerDate.getPersianLongDate());// دوشنبه  13  خرداد  1370
                        Log.d(TAG, "onDateSelected: " + persianPickerDate.getPersianMonthName());//خرداد
                        Log.d(TAG, "onDateSelected: " + PersianCalendarUtils.isPersianLeapYear(persianPickerDate.getPersianYear()));//true
                        Toast.makeText(context, persianPickerDate.getPersianYear() + "/" + persianPickerDate.getPersianMonth() + "/" + persianPickerDate.getPersianDay(), Toast.LENGTH_SHORT).show();
                    }

                    @Override
                    public void onDismissed() {

                    }
                });

        picker.show();
        ```
