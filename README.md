# Tableau URL actions: tightening feedback loops and deep linking

## Biography

Brian Vancil trained as a physicist, then taught high school science before burning out, and serendipitously ended up in a job that used Tableau for social good. They pivoted to a data science career and now work for the University of Kansas in Analytics, Institutional Research, & Effectiveness as a data scientist.

![headshot of male-presenting person with a cheesy smile, curly moustache, and a bowtie](presentation/images/headshot_Brian-Vancil.jpg)

## Abstract

We present how to use Tableau URL actions to (1) pre-fill forms with data fields or (2) deep link into other systems to *informate* (i.e. auto*mate* connections to other sources of *inform*ation) your data workflows. The presentation will focus on basic Tableau functionality but push you to stretch how you use Tableau to interact with your information technology environment.

Presentation given to the Higher Education Tableau User Group on 2023-10-17.

### Personal links

- Sadly bare [Tableau Public](https://public.tableau.com/app/profile/brian.vancil)
- [LinkedIn](https://www.linkedin.com/in/brianvancil/)
- [Mastodon/Fediverse](https://fosstodon.org/@bvancil)

## Prior art

- [*informate*](https://en.wikipedia.org/wiki/Informating) was coined by Shoshana Zuboff
- Eric Parker. [URL Actions: Use Tableau Like a True App — OneNumber](https://onenumber.biz/blog-1/2019/4/17/url-actions-use-tableau-like-a-true-app)

## Case studies of external systems

Although the method can be used for any system that uses `GET`-style URLs, we profile a few different options in case studies.

### Google Forms

Example: Providing feedback on dashboards.

You may view the [dashboard](https://public.tableau.com/app/profile/brian.vancil/viz/WorldIndicators-FeedbackTest/A), which links to the [survey](https://docs.google.com/forms/d/e/1FAIpQLSdm28hTNGWKTXT5vk1Wmk3c_BuDvsmnShylr6FLGGx0vaQdyw/viewform?usp=pp_url&entry.1727620612=username&entry.838417280=full+name&entry.908520332=A)

We have set up the dashboard to prefill responses using `https://docs.google.com/forms/d/e/1FAIpQLSdm28hTNGWKTXT5vk1Wmk3c_BuDvsmnShylr6FLGGx0vaQdyw/viewform?usp=pp_url&entry.1727620612=`*username*`&entry.838417280=`*full+name*`&entry.908520332=`*A*

Note that Tableau Public prevents dashboards from using the `USERNAME()` function.

#### References

- Trevor Fox. "[Dynamically Pre-fill Google Forms with URL Parameters • Trevor Fox](https://trevorfox.com/2015/06/dynamically-pre-fill-google-forms-with-mailchimp-merge-tags/)."
- Udara Alwis. "[Let’s auto fill Google Forms with URL parameters… | ÇøŋfuzëÐ SøurcëÇødë](https://theconfuzedsourcecode.wordpress.com/2019/11/10/lets-auto-fill-google-forms-with-url-parameters/)".

### Qualtrics

Example: Notifications of bad data.

You can see the [dashboard](https://public.tableau.com/app/profile/brian.vancil/viz/data-quality-test/Dashboard), which links to the [survey](https://kusurvey.ca1.qualtrics.com/jfe/form/SV_a5W6XAleJJG8Mey).

We have set up the dashboard to prefil responses using `https://kusurvey.ca1.qualtrics.com/jfe/form/SV_a5W6XAleJJG8Mey?user=`*username*`&name=`*Full+Name*`&id=`*id*

#### References

- Angel Tazzer. "[Passing URL parameters to a Qualtrics Survey - YouTube](https://www.youtube.com/watch?v=xHG6KJJwJ6w)".
- Qualtrics. "[Passing information via query strings](https://www.qualtrics.com/support/survey-platform/survey-module/survey-flow/standard-elements/passing-information-through-query-strings/)".

### Slate CRM

Example: Editing erroneous data.

#### URL Types

Detail
: `/manage/lookup/record?id=`*personUUID*

Query landing page
: `/manage/query/query?id=`*queryUUID*

Query
: `/manage/query/call?id=`*queryUUID*

Query output
: `/manage/query/run?id=`*queryUUID*`&run=`*runUUID*

Report
: `/manage/report/render?id=`*reportUUID*`&`*parameter1Id*`=`*parameter1Value*`&`...

Report Part
: `/manage/report/part?part=`*partUUID*`

#### References

- [Free Online GUID Generator](https://guidgenerator.com/)
- Slate Knowledge Base. "[Parameters in reports](https://knowledge.technolutions.com/hc/en-us/articles/360033359491-Parameters-in-Reports#using-parameters-in-reports-0-0)".
- Slate Knowledge Base. "[Prepopulating or prefilling forms using query string parameters](https://knowledge.technolutions.com/hc/en-us/articles/360032795252-Prepopulating-or-Prefilling-Forms-Using-Query-String-Parameters)".

## Maintaining

``` bash
quarto render presentation/2023-10-17_bvancil_hetug_tableau-url-actions.qmd
quarto publish gh-pages presentation/2023-10-17_bvancil_hetug_tableau-url-actions.qmd --no-render
```
