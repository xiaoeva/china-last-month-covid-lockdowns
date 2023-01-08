# China's Last Month of Covid-19 Lockdowns 

<img src = "https://github.com/xiaoeva/china-last-month-covid-lockdowns/blob/main/lockdown_animation.gif" width = "75%"/>

## Dataset Introduction

This repository includes data on areas designated as 'high-risk' for COVID-19 in China from November 24, 2022 to December 23, 2022. "High-risk" means residents at those locations must quarantine at home (more on that below). 

The data was scraped from the following URLs:
* http://bmfw.www.gov.cn/yqfxdjcx/index.html (retired around December 15th)
* http://bmfw.www.gov.cn/yqfxdjcx/risk.html (retired after December 23rd)

Both websites are hosted by China's State Council, but the data is attributed to the country's National Health Commission (中华人民共和国国家卫生健康委员会). I started scraping the data on November 24th and had to stop December 23rd, because the NHC stopped publishing high-risk areas as the country lifted its zero-covid policy.

### What does "high risk" (高风险地区) mean?

High-risk COVID-19 areas are places where more than 10 cases are discovered within a 2-week period ([source in Chinese](https://web.archive.org/web/20220308145717/https://www.sc.gov.cn/10462/10464/13722/2021/11/10/d0c69ea270c643578fa1fbc77e4a2272.shtml)). In such areas, residents are not supposed to leave their house and necessary services are delivered to their door (ex: grocery delivery) ([source in Chinese](https://web.archive.org/web/20220810110632/http://www.gov.cn/fuwu/2022-07/30/content_5703632.htm))

Since the word "lockdown" can mean a variety of things, I decided to focus on high-risk areas because they are the strictest level of quarantine and lockdown in China.

### Repository Files

The "raw_data" directory includes daily lockdown data that I scraped without any post-processing or data cleaning. The "tidy_data" directory includes the cleaned and reformatted version of the dataset, with the following columns:

#### Municipality/Province

The largest administrative unit lockdown data was characterized under. It includes China's major municipalities like Beijing and Chongqing, and all provinces and regions, including Xinjiang and Tibet. **Note:** Hong Kong and Macau are not included in this dataset.

#### District

This is the second largest administrative unit, which includes city districts but also even more local data at the 街道 level. But it can also refer to large swaths of land as well, like Karakax County (墨玉县) in Hotan, or Xinjiang Production and Construction Corps land units (ex: 新疆生产建设兵团第八师134团). 

I chose to format this column as Municipality/Province + District (ex: 北京市昌平区天通苑北街道) to make it easy to identify and match which districts belonged where. It also made it easier to map the data.

#### Address

This is the most specific location data from the National Health Commission. I added up the number of high-risk addresses published to calculate the number of places under strict lockdown in China every day.

## Data Cleaning Process

### Duplicate Addresses

### Inconsistent Naming for Provinces

### Punctuation Issues

## Mapping with Amap (高德地图)

To map lockdowns on the district level, I used Amap's Point of Interest Web API, which you can find [here](https://lbs.amap.com/api/webservice/guide/api/search). 

## Other Notes about the Dataset

### Spike in addresses on December 2nd






