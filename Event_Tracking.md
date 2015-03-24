# Event Tracking #
With Event Tracking, it is possible to record user interactions with website elements, for example elements in a Flash website, an embedded video player, embedded AJAX page elements, Page gadgets, File downloads, etc.  You track interactions by attaching the method call (available in urchin.js tracking code) to the particular UI element you want to track.
Event Tracking reports are grouped under the 'Content Optimization\Event Tracking' reporting section:
  * Hosts and Pages (Host|Page vs Events, Unique Events, Value, Avg.value)
  * Categories (Category|Action|Label vs Events, Unique Events ("visits with category"), Value, Avg.value)
  * Actions (Action|Label|Category vs Events, Unique Events ("visits with category/action"), Value, Avg.value)
  * Labels (Label|Action|Category vs Events, Unique Events ("visits with category/action/label"), Value, Avg.value)
  * Trending (Total Events, Visits with Events)

## Event Tracking design ##

### "Unique Events" metric ###
The 'Unique Events' metric, which should be read as "Visits with ...", shows the number of visits in which each unique combination of _category/action/label_ occurs. It is calculated per-session, for each level in the event hierarchy. For example the following sessions with events will generate the following stats:

```
Visit 1
videos/play/Movie1
videos/play/Movie2
trailers/play/Movie1
ads/click/Ad1
ads/click/Ad1

Visit 2
videos/play/Movie1
ads/click/Ad1
ads/click/Ad2

Visit 3
<no events>

2 unique events total (2 visits with events)

Categories
2 unique events in 'videos' category
1 unique event in 'trailers' category
2 unique events in 'ads' category

Actions
3 unique events for 'play' action (2 visits with 'play' action in 'videos' category and 1 visit in 'trailers' category) 
2 unique events for 'click' action

Labels
3 unique events with 'Movie1' label (2 visits with 'videos/play' action and 1 visit with 'trailers/play' action)
1 unique event with 'Movie2' label
2 unique events with 'Ad1' label
1 unique event with 'Ad2' label
```

## Setting Up Event Tracking ##

Ensure your website is configured for tracking with **an updated urchin.js tracking code** http://code.google.com/p/urchin-web-analytics-software/source/browse/trunk/urchin.js. (<font color='red'>_<b>TBD</b> </font>)_

Refer to the Install Guide ('''Using Urchin with UTM Tracking''' section) for details.

Call the `__utmTrackEvent()` method in the source code for every element(object) of the website to be tracked with Event Tracking.    `__utmTrackEvent()` method specification:   utmTrackEvent(cat, action, label, value, page), where
  * cat(category, required) - name for the group of objects to be tracked (e.g.: Video, Audio, etc.)
  * action (required) - action is attached to an object and represent the action performed on the object (e.g.: Play, Stop, etc.)
  * label (optional) - additional info about the event (e.g.: video's title, result of the action(change view -> satelite), etc)
  * value (optional) - numeric value of the action
  * page (optional) - use to override the page to which the event is attributed (current page by default). For example, to group the events under some virtual page hierarchy.

_Example:_

Part of the script for tracking `Video` "Play" event:

`<a href="javascript:document.movie1.Play();" onClick="__utmTrackEvent('Video','Play','My Video Title');">Play</a>`