## This assignment is about Scraping the Data from the website....

#### What is WebScraping?
 WebScraping is the process of extracting and parsing data from the websites.

#### Process for scraping the data from the website

  * Html website
  * Webscraping
  * Data
  
<p>--First of all import requests library as well
  import beautifulSoup from bs4 in Python library</p>

```
import requests
from bs4 import BeautifulSoup
```

<p>--drop the website link with variable name that you want to retrive the datas from the website</p>

```
url='https://www.flipkart.com/search?q=laptop&sid=6bo%2Cb5g&as=on&as-show=on&otracker=AS_QueryStore_OrganicAutoSuggest_1_2_na_na_na&otracker1=AS_QueryStore_OrganicAutoSuggest_1_2_na_na_na&as-pos=1&as-type=RECENT&suggestionId=laptop%7CLaptops&requestId=d90b38b4-fc5f-4271-885b-25480dafd13e&as-searchtext=la'
```

#### Want to Know the response from the respective websites that you want to Scrap the data use requests library </p>

```
resp=requests.get(url)
```

#### BeautifulSoup library is that it is built on the top of html parsing libraries like html,lxml etc..</p>

```
soup=BeautifulSoup(resp.text)
```

#### Soup library comes with html code from the website,then from that-you can select the data that you want -like in my given website link,I collected 6columns of dataset from the website the productname,price,spec.rating...</p>

```
product_name=soup.select('._4rR01T')
```

```
product_price=soup.select('._1_WHN1')
```

```
Graphics_card=soup.select('.rgWa7D:nth-child(1)')
```

```
Display=soup.select('.rgWa7D:nth-child(5)')
```

```
RAM=soup.select('.rgWa7D:nth-child(2)')
```

```
Rating=soup.select('._2_R_DZ span span:nth-child(1)')
```

#### After this,import pandas as np that can be change to Data's into DataFrame

```
import pandas as pd
```

#### i changed product_name(data) into the DataFrame with variable called df

```
df=pd.DataFrame(product_name,columns=['product_name'])
```

#### Then call the df variable,that you can see product_name printed columns wise

------------------------------------

#### Same as like product_name,we can change all other datas into dataframe

```
df['product_price']=product_price
```

```
df['Graphics_card']=Graphics_card
```

```
df['RAM']=RAM
```

```
df['Display']=Display
```

```
df['Rating']=Rating
```

#### After all datas stored as dataframe,its shows like

```
product_name                                     	product_price	       Graphics_card	                 RAM	               Display	                      Rating
0	MSI Stealth 15M Core i7 11th Gen - (16 GB/1 TB...	[₹1,20,990]	[Intel Core i7 Processor (11th Gen)]	[16 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[26 Ratings ]
1	Lenovo IdeaPad Gaming 3 Core i5 11th Gen - (8 ...	[₹65,990]	[Intel Core i5 Processor (11th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[91 Ratings ]
2	ASUS VivoBook 15 Core i3 10th Gen - (8 GB/1 TB...	[₹29,990]	[Intel Core i3 Processor (10th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[126 Ratings ]
3	Lenovo IdeaPad 3 Core i3 10th Gen - (8 GB/256 ...	[₹35,990]	[Intel Core i3 Processor (10th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 Inch) Display]	[2,839 Ratings ]
4	ASUS VivoBook 15 (2022) Core i3 11th Gen - (8 ...	[₹38,990]	[Intel Core i3 Processor (11th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[89 Ratings ]
5	HP Core i3 11th Gen - (8 GB/512 GB SSD/Windows...	[₹42,990]	[Intel Core i3 Processor (11th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[1,002 Ratings ]
6	ASUS VivoBook 15 (2022) Core i3 10th Gen - (8 ...	[₹35,990]	[Intel Core i3 Processor (10th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[1,683 Ratings ]
7	acer Aspire 7 Core i5 10th Gen - (8 GB/512 GB ...	[₹52,990]	[Free upgrade to Windows 11 when available]	[Intel Core i5 Processor (10th Gen)]	[512 GB SSD]	[12,050 Ratings ]
8	Lenovo IdeaPad 3 Core i3 11th Gen - (8 GB/512 ...	[₹40,990]	[Intel Core i3 Processor (11th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[670 Ratings ]
9	DELL Inspiron Athlon Dual Core 3050U - (8 GB/2...	[₹32,990]	[AMD Athlon Dual Core Processor]	[8 GB DDR4 RAM]	[39.62 cm (15.6 Inch) Display]	[110 Ratings ]
10	HP Ryzen 3 Dual Core 3250U - (8 GB/256 GB SSD/...	[₹34,990]	[AMD Ryzen 3 Dual Core Processor]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[2,705 Ratings ]
11	MSI GF63 Thin Core i5 10th Gen - (8 GB/1 TB HD...	[₹53,990]	[Intel Core i5 Processor (10th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[1,161 Ratings ]
12	Infinix INBook X1 Core i3 10th Gen - (8 GB/256...	[₹29,990]	[Intel Core i3 Processor (10th Gen)]	[8 GB LPDDR4X RAM]	[35.56 cm (14 inch) Display]	[3,449 Ratings ]
13	ASUS VivoBook 15 (2022) Celeron Quad Core - (4...	[₹27,990]	[Intel Celeron Quad Core Processor]	[4 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[37 Ratings ]
14	HP Ryzen 5 Hexa Core 5500U - (8 GB/512 GB SSD/...	[₹48,990]	[AMD Ryzen 5 Hexa Core Processor]	[8 GB DDR4 RAM]	[35.56 cm (14 inch) Display]	[479 Ratings ]
15	ASUS TUF Dash F15 (2021) Core i5 11th Gen - (1...	[₹84,990]	[Intel Core i5 Processor (11th Gen)]	[16 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[281 Ratings ]
16	Lenovo Core i3 10th Gen - (8 GB/512 GB SSD/Win...	[₹38,990]	[Intel Core i3 Processor (10th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[166 Ratings ]
17	HP Core i3 11th Gen - (8 GB/256 GB SSD/Windows...	[₹38,990]	[Intel Core i3 Processor (11th Gen)]	[8 GB DDR4 RAM]	[35.56 cm (14 inch) Display]	[1,169 Ratings ]
18	Infinix INBook X1 Core i3 10th Gen - (8 GB/256...	[₹29,990]	[Intel Core i3 Processor (10th Gen)]	[8 GB LPDDR4X RAM]	[35.56 cm (14 inch) Display]	[3,449 Ratings ]
19	MSI GF63 Thin Hexa Core i5 10th Gen - (8 GB/1 ...	[₹58,990]	[Intel Hexa Core i5 Processor (10th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[2,881 Ratings ]
20	ASUS Ryzen 3 Dual Core 3250U 3rd Gen - (8 GB/2...	[₹33,990]	[AMD Ryzen 3 Dual Core Processor (3rd Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[3,188 Ratings ]
21	ASUS VivoBook Ultra 14 (2022) Core i5 11th Gen...	[₹55,990]	[Intel Core i5 Processor (11th Gen)]	[16 GB DDR4 RAM]	[35.56 cm (14 inch) Display]	[85 Ratings ]
22	ASUS VivoBook Core i3 11th Gen - (8 GB/256 GB ...	[₹34,990]	[Intel Core i3 Processor (11th Gen)]	[8 GB DDR4 RAM]	[35.56 cm (14 Inch) Display]	[166 Ratings ]
23	Lenovo IdeaPad Gaming 3i Core i7 11th Gen - (8...	[₹88,990]	[Intel Core i7 Processor (11th Gen)]	[8 GB DDR4 RAM]	[39.62 cm (15.6 inch) Display]	[8 Ratings ]
```

### Finally save this dataframe file as laptopdetails.csv

```
df.to_csv('laptopdetails.csv')
```



## WebCleaning


## After saved as .csv,call the file clean the data that contain unwanted letters,symbols,words we can remove it using strip with help of pandas

### for Exxampe

```
Unnamed: 0	product_name	                                  product_price                               	Graphics_card	                                                    RAM	                                        Display	                Rating
0	0	MSI Stealth 15M Core i7 11th Gen - (16 GB/1 TB...	<div class="_30jeq3 _1_WHN1">₹1,20,990</div>	<li class="rgWa7D">Intel Core i7 Processor (11...	<li class="rgWa7D">16 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>26 Ratings </span>
1	1	Lenovo IdeaPad Gaming 3 Core i5 11th Gen - (8 ...	<div class="_30jeq3 _1_WHN1">₹65,990</div>	<li class="rgWa7D">Intel Core i5 Processor (11...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>91 Ratings </span>
2	2	ASUS VivoBook 15 Core i3 10th Gen - (8 GB/1 TB...	<div class="_30jeq3 _1_WHN1">₹29,990</div>	<li class="rgWa7D">Intel Core i3 Processor (10...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>126 Ratings </span>
3	3	Lenovo IdeaPad 3 Core i3 10th Gen - (8 GB/256 ...	<div class="_30jeq3 _1_WHN1">₹35,990</div>	<li class="rgWa7D">Intel Core i3 Processor (10...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 Inch) Displa...	<span>2,839 Ratings </span>
4	4	ASUS VivoBook 15 (2022) Core i3 11th Gen - (8 ...	<div class="_30jeq3 _1_WHN1">₹38,990</div>	<li class="rgWa7D">Intel Core i3 Processor (11...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>89 Ratings </span>
5	5	HP Core i3 11th Gen - (8 GB/512 GB SSD/Windows...	<div class="_30jeq3 _1_WHN1">₹42,990</div>	<li class="rgWa7D">Intel Core i3 Processor (11...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>1,002 Ratings </span>
6	6	ASUS VivoBook 15 (2022) Core i3 10th Gen - (8 ...	<div class="_30jeq3 _1_WHN1">₹35,990</div>	<li class="rgWa7D">Intel Core i3 Processor (10...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>1,683 Ratings </span>
7	7	acer Aspire 7 Core i5 10th Gen - (8 GB/512 GB ...	<div class="_30jeq3 _1_WHN1">₹52,990</div>	<li class="rgWa7D">Free upgrade to Windows 11 ...	<li class="rgWa7D">Intel Core i5 Processor (10...	<li class="rgWa7D">512 GB SSD</li>	<span>12,050 Ratings </span>
8	8	Lenovo IdeaPad 3 Core i3 11th Gen - (8 GB/512 ...	<div class="_30jeq3 _1_WHN1">₹40,990</div>	<li class="rgWa7D">Intel Core i3 Processor (11...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>670 Ratings </span>
9	9	DELL Inspiron Athlon Dual Core 3050U - (8 GB/2...	<div class="_30jeq3 _1_WHN1">₹32,990</div>	<li class="rgWa7D">AMD Athlon Dual Core Proces...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 Inch) Displa...	<span>110 Ratings </span>
10	10	HP Ryzen 3 Dual Core 3250U - (8 GB/256 GB SSD/...	<div class="_30jeq3 _1_WHN1">₹34,990</div>	<li class="rgWa7D">AMD Ryzen 3 Dual Core Proce...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>2,705 Ratings </span>
11	11	MSI GF63 Thin Core i5 10th Gen - (8 GB/1 TB HD...	<div class="_30jeq3 _1_WHN1">₹53,990</div>	<li class="rgWa7D">Intel Core i5 Processor (10...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>1,161 Ratings </span>
12	12	Infinix INBook X1 Core i3 10th Gen - (8 GB/256...	<div class="_30jeq3 _1_WHN1">₹29,990</div>	<li class="rgWa7D">Intel Core i3 Processor (10...	<li class="rgWa7D">8 GB LPDDR4X RAM</li>	<li class="rgWa7D">35.56 cm (14 inch) Display<...	<span>3,449 Ratings </span>
13	13	ASUS VivoBook 15 (2022) Celeron Quad Core - (4...	<div class="_30jeq3 _1_WHN1">₹27,990</div>	<li class="rgWa7D">Intel Celeron Quad Core Pro...	<li class="rgWa7D">4 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>37 Ratings </span>
14	14	HP Ryzen 5 Hexa Core 5500U - (8 GB/512 GB SSD/...	<div class="_30jeq3 _1_WHN1">₹48,990</div>	<li class="rgWa7D">AMD Ryzen 5 Hexa Core Proce...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">35.56 cm (14 inch) Display<...	<span>479 Ratings </span>
15	15	ASUS TUF Dash F15 (2021) Core i5 11th Gen - (1...	<div class="_30jeq3 _1_WHN1">₹84,990</div>	<li class="rgWa7D">Intel Core i5 Processor (11...	<li class="rgWa7D">16 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>281 Ratings </span>
16	16	Lenovo Core i3 10th Gen - (8 GB/512 GB SSD/Win...	<div class="_30jeq3 _1_WHN1">₹38,990</div>	<li class="rgWa7D">Intel Core i3 Processor (10...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>166 Ratings </span>
17	17	HP Core i3 11th Gen - (8 GB/256 GB SSD/Windows...	<div class="_30jeq3 _1_WHN1">₹38,990</div>	<li class="rgWa7D">Intel Core i3 Processor (11...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">35.56 cm (14 inch) Display<...	<span>1,169 Ratings </span>
18	18	Infinix INBook X1 Core i3 10th Gen - (8 GB/256...	<div class="_30jeq3 _1_WHN1">₹29,990</div>	<li class="rgWa7D">Intel Core i3 Processor (10...	<li class="rgWa7D">8 GB LPDDR4X RAM</li>	<li class="rgWa7D">35.56 cm (14 inch) Display<...	<span>3,449 Ratings </span>
19	19	MSI GF63 Thin Hexa Core i5 10th Gen - (8 GB/1 ...	<div class="_30jeq3 _1_WHN1">₹58,990</div>	<li class="rgWa7D">Intel Hexa Core i5 Processo...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>2,881 Ratings </span>
20	20	ASUS Ryzen 3 Dual Core 3250U 3rd Gen - (8 GB/2...	<div class="_30jeq3 _1_WHN1">₹33,990</div>	<li class="rgWa7D">AMD Ryzen 3 Dual Core Proce...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>3,188 Ratings </span>
21	21	ASUS VivoBook Ultra 14 (2022) Core i5 11th Gen...	<div class="_30jeq3 _1_WHN1">₹55,990</div>	<li class="rgWa7D">Intel Core i5 Processor (11...	<li class="rgWa7D">16 GB DDR4 RAM</li>	<li class="rgWa7D">35.56 cm (14 inch) Display<...	<span>85 Ratings </span>
22	22	ASUS VivoBook Core i3 11th Gen - (8 GB/256 GB ...	<div class="_30jeq3 _1_WHN1">₹34,990</div>	<li class="rgWa7D">Intel Core i3 Processor (11...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">35.56 cm (14 Inch) Display<...	<span>166 Ratings </span>
23	23	Lenovo IdeaPad Gaming 3i Core i7 11th Gen - (8...	<div class="_30jeq3 _1_WHN1">₹88,990</div>	<li class="rgWa7D">Intel Core i7 Processor (11...	<li class="rgWa7D">8 GB DDR4 RAM</li>	<li class="rgWa7D">39.62 cm (15.6 inch) Displa...	<span>8 Ratings </span>
```
In above example,some of the data contain unwanted words,letters,symbols...so i removed it with the help of strip

```
gf['product_price']=gf['product_price'].str.strip('<div class=""_30jeq3 _1_WHN1""></div>').astype(str)
```

##### In above code,call the column name and column data strip the unwanted words or symbols to store as relevant datatype

### After clean the datas in dataframe....it shows like

```
Unnamed: 0	product_name	                        product_price	       Graphics_card	                  RAM	                 Display	             Rating
0	0	MSI Stealth 15M Core i7 11th Gen - (16 GB/1 TB...	₹1,20,99	Intel Core i7 Processor (11th Gen)	16 GB DDR4 RAM	39.62 cm (15.6 inch) Display	26 Ratings
1	1	Lenovo IdeaPad Gaming 3 Core i5 11th Gen - (8 ...	₹65,99	Intel Core i5 Processor (11th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	91 Ratings
2	2	ASUS VivoBook 15 Core i3 10th Gen - (8 GB/1 TB...	₹29,99	Intel Core i3 Processor (10th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	126 Ratings
3	3	Lenovo IdeaPad 3 Core i3 10th Gen - (8 GB/256 ...	₹35,99	Intel Core i3 Processor (10th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 Inch) Display	2,839 Ratings
4	4	ASUS VivoBook 15 (2022) Core i3 11th Gen - (8 ...	₹38,99	Intel Core i3 Processor (11th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	89 Ratings
5	5	HP Core i3 11th Gen - (8 GB/512 GB SSD/Windows...	₹42,99	Intel Core i3 Processor (11th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	1,002 Ratings
6	6	ASUS VivoBook 15 (2022) Core i3 10th Gen - (8 ...	₹35,99	Intel Core i3 Processor (10th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	1,683 Ratings
7	7	acer Aspire 7 Core i5 10th Gen - (8 GB/512 GB ...	₹52,99	Free upgrade to Windows 11 when available	Intel Core i5 Processor (10th Gen)	512 GB SS	12,050 Ratings
8	8	Lenovo IdeaPad 3 Core i3 11th Gen - (8 GB/512 ...	₹40,99	Intel Core i3 Processor (11th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	670 Ratings
9	9	DELL Inspiron Athlon Dual Core 3050U - (8 GB/2...	₹32,99	AMD Athlon Dual Core Processo	8 GB DDR4 RAM	39.62 cm (15.6 Inch) Display	110 Ratings
10	10	HP Ryzen 3 Dual Core 3250U - (8 GB/256 GB SSD/...	₹34,99	AMD Ryzen 3 Dual Core Processo	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	2,705 Ratings
11	11	MSI GF63 Thin Core i5 10th Gen - (8 GB/1 TB HD...	₹53,99	Intel Core i5 Processor (10th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	1,161 Ratings
12	12	Infinix INBook X1 Core i3 10th Gen - (8 GB/256...	₹29,99	Intel Core i3 Processor (10th Gen)	8 GB LPDDR4X RAM	35.56 cm (14 inch) Display	3,449 Ratings
13	13	ASUS VivoBook 15 (2022) Celeron Quad Core - (4...	₹27,99	Intel Celeron Quad Core Processo	4 GB DDR4 RAM	39.62 cm (15.6 inch) Display	37 Ratings
14	14	HP Ryzen 5 Hexa Core 5500U - (8 GB/512 GB SSD/...	₹48,99	AMD Ryzen 5 Hexa Core Processo	8 GB DDR4 RAM	35.56 cm (14 inch) Display	479 Ratings
15	15	ASUS TUF Dash F15 (2021) Core i5 11th Gen - (1...	₹84,99	Intel Core i5 Processor (11th Gen)	16 GB DDR4 RAM	39.62 cm (15.6 inch) Display	281 Ratings
16	16	Lenovo Core i3 10th Gen - (8 GB/512 GB SSD/Win...	₹38,99	Intel Core i3 Processor (10th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	166 Ratings
17	17	HP Core i3 11th Gen - (8 GB/256 GB SSD/Windows...	₹38,99	Intel Core i3 Processor (11th Gen)	8 GB DDR4 RAM	35.56 cm (14 inch) Display	1,169 Ratings
18	18	Infinix INBook X1 Core i3 10th Gen - (8 GB/256...	₹29,99	Intel Core i3 Processor (10th Gen)	8 GB LPDDR4X RAM	35.56 cm (14 inch) Display	3,449 Ratings
19	19	MSI GF63 Thin Hexa Core i5 10th Gen - (8 GB/1 ...	₹58,99	Intel Hexa Core i5 Processor (10th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	2,881 Ratings
20	20	ASUS Ryzen 3 Dual Core 3250U 3rd Gen - (8 GB/2...	₹33,99	AMD Ryzen 3 Dual Core Processor (3rd Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	3,188 Ratings
21	21	ASUS VivoBook Ultra 14 (2022) Core i5 11th Gen...	₹55,99	Intel Core i5 Processor (11th Gen)	16 GB DDR4 RAM	35.56 cm (14 inch) Display	85 Ratings
22	22	ASUS VivoBook Core i3 11th Gen - (8 GB/256 GB ...	₹34,99	Intel Core i3 Processor (11th Gen)	8 GB DDR4 RAM	35.56 cm (14 Inch) Display	166 Ratings
23	23	Lenovo IdeaPad Gaming 3i Core i7 11th Gen - (8...	₹88,99	Intel Core i7 Processor (11th Gen)	8 GB DDR4 RAM	39.62 cm (15.6 inch) Display	8 Ratings
```

### Save the file as .csv

```
gf.to_csv('lapdetails.csv')
```

