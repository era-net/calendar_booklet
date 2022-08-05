# **CALENDAR_BOOKLET**
Calendar booklet generator to write down working hours for each year.

## **Features**
- built in holidays for several [regions](https://github.com/dr-prodigy/python-holidays#available-countries)
- custom events via MS Excel or csv file
- custom event colors

## **Getting started**
Edit the main settings at the top of the script.
<br>
main.py
```python
year = 2022                     # year to be generated
date_format = "%m/%d/%y"        # date format for the pdf doc
date_delimiter = str(date_format.split("%")[1][1]) # do not change
holiday_country = "US"          # United States of America (full list below)
holiday_subdiv = "CA"           # California (full list below)
include_holidays = True         # Set to true so the results are visible
include_custom_events = False   # not needed for now
include_page_no = False         # not needed for now
language = "en"                 # support for "en" and "de" for now
```
> **NOTE**: A full list of all supported holiday countries can be found in the [holidays repo](https://github.com/dr-prodigy/python-holidays#available-countries).

After you run `main.py` with the settings above a file named `booklet.pdf` will appear. This is the most simple type of usage for this program.

## **Adding custom events**
To add custom events like birthdays or other special dates that occur every year, open a blank excel or csv file. Let's say we want to add a custom event on September 5th each year.
| event name               | day number | month number |
| ------------------------ |       ---: |         ---: |
| my custom event          |          5 |            9 |

Once done, save the file in the events folder in the project directory. We'll call it `test.csv` for now.

> **NOTE**: Do not forget to set `include_custom_events = True` in `main.py`.

Run the script and search for the event we just added in the pdf document.

## **Let's add some color**
To color your events, open the `colors.json` file in the `inc` directory. Now set the key of the json object to be exactly the same as the file name you wish to add color to.
```json
{
    "test.xlsx": {
        "font": "#ff0000",
        "background": "#c5e0b3"
    }
}
```

Above you see the pattern that is needed to bring color to your events. Copy the pattern above into your colors.json file and try it out.

Note that we named the json object as the file in the `events` directory. This is necessary so the script knows wich event file should have the colors that were defined.

If you followed the instructions accordingly, you should see that in september your custom event was added succesfully.
