# China's Last Month of Covid-19 Lockdowns 

<img src = "https://github.com/xiaoeva/china-last-month-covid-lockdowns/blob/main/lockdown_animation.gif" width = "75%"/>

### Dataset Introduction

This repository shares official data released by the Chinese government from November 24, 2022 to December 23, 2022 on places in China that have been designated as 'high-risk' for COVID-19. "High-risk" means residents at those locations must quarantine at home (more on that below). 

The data was scraped from the following websites:
* http://bmfw.www.gov.cn/yqfxdjcx/index.html (retired around December 15th)
* http://bmfw.www.gov.cn/yqfxdjcx/risk.html (retired after December 23rd)

Both are hosted by China's State Council, but the data comes from the National Health Commission (中华人民共和国国家卫生健康委员会). I started scraping the data on November 24th and had to stop December 23rd, because the NHC stopped publishing high-risk areas as the country lifted its zero-covid policy.

#### What does "high risk" (高风险地区) mean?

High-risk COVID-19 areas are places where more than 10 cases are discovered within a 2-week period ([source in Chinese](https://web.archive.org/web/20220308145717/https://www.sc.gov.cn/10462/10464/13722/2021/11/10/d0c69ea270c643578fa1fbc77e4a2272.shtml)). In such areas, residents cannot leave their homes and necessary services are delivered to their door (ex: grocery delivery) ([source in Chinese](https://web.archive.org/web/20220810110632/http://www.gov.cn/fuwu/2022-07/30/content_5703632.htm))

Since the word "lockdown" can mean a variety of things, I decided to focus on high-risk areas because they are the strictest level of quarantine and lockdown in China.

#### Data Files

The "raw_data" directory includes daily lockdown data that I scraped without any post-processing or data cleaning. The "tidy_data" directory includes the cleaned and reformatted version of the dataset, with the following columns:

##### Municipality/Province

The largest administrative unit lockdown data was characterized under. It includes China's major municipalities like Beijing and Chongqing, and all provinces and regions, including Xinjiang and Tibet. **Note:** Hong Kong and Macau are not included in this dataset.

##### District

This is the second largest administrative unit, which includes city districts but also even more local data at the 街道 level. But it can also refer to large swaths of land, like Karakax County (墨玉县) in Hotan, or Xinjiang Production and Construction Corps land units (ex: 新疆生产建设兵团第八师134团). 

I chose to format this column as Municipality/Province + District (ex: 北京市昌平区天通苑北街道) to make it easy to identify and match which districts belonged where. It also made it easier to map the data.

##### Address

This is the most specific location data from the National Health Commission. I added up the number of high-risk addresses published to calculate the number of places under strict lockdown in China every day.

### Data Cleaning Process

Here's some stuff to look out for if you decide to process the raw data yourself, or if you are curious about what was changed in the tidy_data versions:

#### Duplicate Addresses

Per day, there shouldn't be any addresses that are repeated but there are, perhaps due to human error when lockdown data is compiled by the National Health Commission.

There are also duplicate addresses that *appear* to be different but are actually identical. This happened a lot and it usually meant there was district-level location data included in the address, for example: 回民区***战备路社区人行小区3号楼*** vs. 战备路社区人行小区3号楼. 

#### Inconsistent Naming for Provinces

When the first website I scraped was taken down, I switched to the second URL, which was formatted similarly but not identically to the first one. The names of some municipalities and provinces were different, such as 云南 vs. 云南省. 

#### Punctuation Issues

I found stray punctuation at the end of some lockdown addresses, like: "新源道街道和平丽景社区盛德金地小区C座。" 

Also, some addresses were bundled together under the same district by semi-colon (note: ；not ; <- first one comes from the Chinese keyboard) instead of listed separately. So I separated those addresses out by splitting the addresses via semi-colon.

### Data Scraping Process

I used Selenium to scrape the two State Council websites. I tried to find historical data on the [Wayback Machine](https://web.archive.org/web/20230000000000*/http://bmfw.www.gov.cn/yqfxdjcx/index.html) but it was very inconsistent and I even struggled to take snapshots of the website when it was still up.

If you're curious about what the two different websites looked like, I have some PDF copies stored in the backup_PDFs directory. Sadly, I wasn't able to PDF all the data for each day. 

### Mapping with Amap (高德地图)

To map lockdowns on the district level, I used Amap's Point of Interest Web API, which you can find [here](https://lbs.amap.com/api/webservice/guide/api/search). 

### Other Notes about the Dataset

#### Spike in addresses on December 2nd

<img src ="https://github.com/xiaoeva/china-last-month-covid-lockdowns/blob/main/changing_lockdown_numbers_daily.png" width = "50%" alt="Animated map showing how the number of lockdowns in China changed over November-December 2022" alt="A graph showing the daily changes in number of high-risk areas in China"/>

As you can see in the animation up top, there's a huge spike in cases on December 2nd. The change mainly comes from Guangdong province which went from 1,969 high-risk areas on December 1st to **7,659** on December 2nd. This was at a time when China was starting to [*loosen*](https://www.nytimes.com/2022/12/01/world/asia/china-covid-protests-restrictions.html) its covid policies though. So what happened?

Instead of listing an entire building as being high-risk, a lot of places in Guangdong began designating specific apartments or stores. So while there were probably fewer places under lockdown, more addresses were being listed as high-risk. I couldn't think of a good way to reflect this in the data, but if you have any ideas, I would love to hear them!











