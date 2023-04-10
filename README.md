# awesome_android_persian
A collection of Persian Android Libraries

## Shamsi Calenadars (solar calendars)
### 1. [persianDate By SamanZamani](https://github.com/samanzamani/PersianDate)


example:
```java
PersianDate pdate = new PersianDate();
PersianDateFormat pdformater1 = new PersianDateFormat('Y/m/d');
pdformater1.format(pdate);//1396/05/20

PersianDateFormat pdformater2 = new PersianDateFormat('y F j');
pdformater2.format(pdate);//۱۹ تیر ۹۶
```

### 2. [persian date-time by Mohammad Fathi](https://github.com/mfathi91/persian-date-time)
substitute for `DateTime` library in java. usage example:

```java
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
### 1. [Persian-date-picker-dialog By Ali Abdollahi](https://github.com/aliab/Persian-Date-Picker-Dialog)
![date picker by ali abdollahi](https://raw.githubusercontent.com/aliab/Persian-Date-Picker-Dialog/master/screenshot/heroimage.jpg)
example:

```java
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

### 2. [PersianRangeDatePicker by Ali Sardari](https://github.com/ali-sardari/PersianRangeDatePicker)

![range date picker farsi](https://github.com/ali-sardari/PersianRangeDatePicker/blob/master/images/range_date_picker2.jpg)
a beautiful date range picker for android in shamsi calendar

example:
```
DatePickerDialog datePickerDialog = new DatePickerDialog(MainActivity.this);
datePickerDialog.setSelectionMode(DateRangeCalendarView.SelectionMode.Range);
//datePickerDialog.setEnableTimePicker(true);
//datePickerDialog.setShowGregorianDate(true);
datePickerDialog.setTextSizeTitle(10.0f);
datePickerDialog.setTextSizeWeek(12.0f);
datePickerDialog.setTextSizeDate(14.0f);
datePickerDialog.setCanceledOnTouchOutside(true);
datePickerDialog.setOnRangeDateSelectedListener(new DatePickerDialog.OnRangeDateSelectedListener() {
        @Override
        public void onRangeDateSelected(PersianCalendar startDate, PersianCalendar endDate) {
            txtStartDate.setText(startDate.getPersianShortDate());
            txtEndDate.setText(endDate.getPersianShortDate());
        }
});

datePickerDialog.showDialog();
```

### 3. [persian date picker by farshad Asgharzadeh](https://github.com/Far5had70/PersianDateRangePicker)
![persian date picker](https://raw.githubusercontent.com/Far5had70/PersianDateRangePicker/master/capture.gif)

usage example:

```java
        Typeface face = Typeface.createFromAsset(getAssets(), "bsans.ttf");
        FragmentManager fragmentManager = getSupportFragmentManager();
        PersianDateRangePicker persianDateRangePicker = new PersianDateRangePicker()
                .setInitTillDate(InitDate.inputPersianDate(1, 3, 1397))
                .setInitFromDate(InitDate.inputPersianDate(1, 1, 1397))
                .setBackgroundColor(getResources().getColor(R.color.green))
                .setButtonTextColor(getResources().getColor(R.color.white))
                .setTabTextColor(getResources().getColor(R.color.white))
                .setTabSelectedTextColor(getResources().getColor(R.color.white))
                .setTabIndicatorColor(getResources().getColor(R.color.white))
                .setWheelTextColor(getResources().getColor(R.color.white_smoke))
                .setWheelTextColorSelected(getResources().getColor(R.color.white))
                .setWheelTextSize(20)
                .setCornerRadius(40)
                .setTypeface(face)
                .setDoneText("تائید")
                .setCanselText("انصراف")
                .setDoneDrawable(getResources().getDrawable(R.drawable.ic_tick))
                .setCanselDeawable(getResources().getDrawable(R.drawable.ic_mult))
                .setCurrentItem(SetCurrentItem.From)
                .setListener(new PersianDateRangePicker.RangeDate() {
                    @Override
                    public void From(int day, int month, int year) {
                        Toast.makeText(MainActivity.this, ""+day+"  "+month+"  "+year, Toast.LENGTH_SHORT).show();
                    }

                    @Override
                    public void TillDate(int day, int month, int year) {
                        Toast.makeText(MainActivity.this, ""+day+"  "+month+"  "+year, Toast.LENGTH_SHORT).show();

                    }

                    @Override
                    public void cansel() {

                    }
                });
        persianDateRangePicker.show(fragmentManager, "PersianDateRangePicker");
```
## Tools
### 1. [prettyPersianNumbers by Yamin Siahmargooei](https://github.com/yamin8000/PrettyPersianNumbers)
converts numbers to persian words
example:
```kotlin
val word1: String = Digits().spellToFarsi(input)
val word2: String = Digits().spellToFarsi(12) // دوازده
//دوازده میلیارد و یک صد و بیست و سه میلیون و سی صد و دوازده هزار و یک صد و بیست و سه
val word3: String = Digits().spellToFarsi(12_123_312_123)
//پنج میلیون و یک صد و بیست و یک هزار و سی صد و بیست و یک
val word4: String = Digits().spellToFarsi("5121321")
//سه ممیز چهارده، صدم
val decimalWord: String = Digits().spelltoFarsi(3.14)
```

### 2. [Random persian name generator by armanyazdi](https://github.com/armanyazdi/persian-names-java)

example: 

```java
System.out.println(PersianNames.fullNameFarsi("m")); // اشکان محمدرضائیان
System.out.println(PersianNames.fullNameFarsi("f")); // مهسا امینی
System.out.println(PersianNames.fullNameFarsi("r")); // بیتا خسروی راد
```

### 3. [Persian Number To Word by mortezaSun](https://github.com/mortezasun/PersianNumberToWordAndroid)
too simple to be true Helper methods to convert number to alphabetic presentations

just copy [this file](https://github.com/mortezasun/PersianNumberToWordAndroid/blob/master/PersianNumberToWord.kt) to your project and you are good to go!


