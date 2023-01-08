# China's Covid-19 Lockdown Data 

![alt text](https://github.com/xiaoeva/china-last-month-covid-lockdowns/lockdown_animation.gif "China's Last Month of Covid-19 Lockdowns")

## Dataset Introduction

This repository includes data on areas designated as 'high-risk' for COVID-19 in China from November 24, 2022 to December 23, 2022. The data was scraped from the following URLs:
* http://bmfw.www.gov.cn/yqfxdjcx/index.html (retired around December 15th)
* http://bmfw.www.gov.cn/yqfxdjcx/risk.html (retired after December 23rd)

Both websites are hosted by China's State Council, but the data is attributed to the country's National Health Commission (中华人民共和国国家卫生健康委员会). I started scraping the data on November 24th and had to stop December 23rd, because the NHC stopped publishing high-risk areas as the country lifted its zero-covid policy.

### What does "high risk" (高风险地区) mean?

  按照国务院联防联控机制《关于调整新冠肺炎疫情分区分级标准实施精准管控措施的通知》的要求，病例长期停留地区(如其居住的居民小区、自然村等)，14天内发生不超过10例的本土确诊病例，该地区划定为中风险地区；若出现10例及以上本土确诊病例则会被划定为高风险地区。

[Source: Sichuan Provincial Government Website on the Wayback Machine](https://web.archive.org/web/20220308145717/https://www.sc.gov.cn/10462/10464/13722/2021/11/10/d0c69ea270c643578fa1fbc77e4a2272.shtml)

High-risk COVID-19 areas are places where more than 10 cases are discovered within a 2-week period. In such areas, residents are not supposed to leave their house and necessary services are delivered to their door (ex: grocery delivery). 

Since the word "lockdown" can mean a variety of things, I decided to focus on high-risk areas because they are the strictest level of quarantine and lockdown in China.

### Repository Files

The "raw_data" directory includes text files storing the data I scraped without any post-processing or data cleaning. The "tidy_data" directory includes the cleaned and reformatted version of the dataset, with the following columns:

#### Municipality/Province

The largest administrative unit lockdown data was characterized under. It includes China's major municipalities like Beijing and Chongqing, and all provinces and regions, including Xinjiang and Tibet. **Note:** Hong Kong and Macau are not included in this dataset.

#### District

This is the second largest administrative unit, which includes districts within municipalities but also even more local data at the 街道 level. But it can also refer to large prefectures as well, like Moyu prefecture (墨玉县) in Hotan, or Xinjiang Production and Construction Corps units (ex: 新疆生产建设兵团第八师134团). 

I chose to format this column as Municipality/Province + District (ex: 北京市昌平区天通苑北街道) to make it easy to identify and match which districts belonged where. It also made it easier to map the data.

#### Address

This is the most specific location data from the National Health Commission. I added up the number of high-risk addresses published to calculate the number of places under strict lockdown in China every day.

## Data Cleaning Process

### Duplicate Addresses

### Inconsistent Naming for Provinces

## Mapping with Amap (高德地图)

To map all district, I used Amap's API, which you can find here: TKTK

## Other Notes about the Dataset

### Spike in addresses on December 2nd




