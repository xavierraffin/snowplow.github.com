---
layout: section
category: product
title: FAQ
weight: 7
---

<a name="top" />
# Frequently asked questions

1. [Does SnowPlow have a graphical user interface to enable me to analyse and visualise web analytics data?](#gui)
2. [Is SnowPlow real-time?](#realtime)
3. [Does implementing SnowPlow on my site effect site performance e.g. page load times?](#loadtimes)
4. [Does SnowPlow use first- or third-party cookies?](#cookies)

<a name="gui" />
## 1. Does SnowPlow have a graphical user interface to enable me to analyse and visualise web analytics data? 

No, currently SnowPlow does not have a GUI. 

For users who are using the [Hive version] [hive-storage] of the [SnowPlow storage] [storage], analysts who want to query the data will need to write those queries in Hive, Pig or Java MapReduce.

There are a number of companies working to build GUIs to work on top of Hadoop. We are watching these developments closely, and hope that to make it easy to integrate these front-ends with SnowPlow in the future, to enable analysts less comfortable with e.g. Hive to use SnowPlow.

For users who are using the [Infobright version] [infobright-storage] of the [SnowPlow storage] [storage], there is a wide range of tools to make it easier for analysts to visualise and query the data direclty in Infobright. (Infobright plugs into anything that can plug into MySQL.)

We are also looking at possibilities of building GUIs to perform repeatable analyses that we see are popular amongst the SnowPlow community. However, we do not believe in general purpose GUIs for web analytics: the whole point of SnowPlow is to free the experienced analyst from the constraints of GUIs (with all their assumptions about how the analyst does and does not want to slice the data), so analysts can have maximum flexibility to slice, dice and model data to his / her heart's content.

[Back to top](#top)

<a name="realtime" />
## 2. Is SnowPlow real-time?
No, currently SnowPlow is not a real-time analytics solution. 

In order to deliver real time analytics, each submodule in SnowPlow (tracker / collector / ETL / storage and analytics) needs to be real time.

There are a number of modules that are real-time already, however:

1. The Javascript tracker works in real-time.
2. The [SnowCannon node.js collector] [snowcannon] is real-time. The clojure collector. A real-time Clojure collector is currently under development, that will run on Amazon's Elastic Beanstalk.

However, in order to deliver real-time analytics, real-time ETL needs to be developed. We are not currently working on this.

[Back to top](#top)

<a name="loadtimes" />
## 3. Does implementing SnowPlow on my site effect site performance e.g. page load times?

SnowPlow will have an impact on site performance, just as implementing any javascript-based tracking (e.g. another web analytics package) will impact site performance. However, we have done everything we can to minimise the effect on site performance.

Pages tracked using SnowPlow have to load the SnowPlow.js file. By hosting this page on Amazon's Cloudfront, the time takent to load the javascript is minimised. In addition, users have the choice to implement syncronous and asyncrounous tracking tags: if users wants to minimise the impact on page load times, for example, they should employ async tracking.

[Back to top](#top)

<a name="cookies" />
## 4. Does SnowPlow use first- or third-party cookies?

It depends which collector you use.

If you use the [Cloudfront collector] [cloudfront-collector], SnowPlow uses 1st party cookies, which are generated by the SnowPlow tracking Javascript running on your domain.

If you use e.g. [SnowCannon node.js collector] [snowcannon], 3rd party cookies will be set that can consistently track users across multiple domains.




[hive-storage]: https://github.com/snowplow/snowplow/tree/master/4-storage/hive-storage
[storage]: https://github.com/snowplow/snowplow/tree/master/4-storage
[infobright-storage]: https://github.com/snowplow/snowplow/tree/master/4-storage/infobright-storage
[snowcannon]: https://github.com/snowplow/snowplow/tree/master/2-collectors
[cloudfront-collector]: https://github.com/snowplow/snowplow/tree/master/2-collectors/cloudfront-collector