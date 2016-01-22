# About #
Dreams is a big part of our life and Alarm clock is one of mostly used features of mobile phones.
Android provides great means of application integration.

# Delelopers Introduction #

If you are developing Night Clock-style application, please add an additional intent to your application main class so it could be launched as an abstract 'Night clock UI'.

So, given 'sleep time recorder' application: user clicks 'go to sleep' button, application records the time in the database and will try to launch this intent to show nice UI. If there will be several applications installed with this Inent filter, user will be automatically prompted which to launch (and optionally set to preferred).

**It will take 3-4 lines of xml code only** but the effect is a real synergy of similar applications!

## Example ##

Include this into your startup activity manifest:
```
<intent-filter>
  <action android:name="android.alarmclock.NightClockUI" />
  <category android:name="android.intent.category.DEFAULT"/>
</intent-filter>
```

Now, any application could start yours with few lines of code:
```
try {

    final Intent i = new Intent();
    i.setAction("android.alarmclock.NightClockUI");
    i.addCategory(Intent.CATEGORY_DEFAULT);
    startActivity(i);

} catch (ActivityNotFoundException e) {
    Log.w("Tag", "No NightClockUI found", e);
}
```

Read more:
http://developer.android.com/guide/topics/intents/intents-filters.html