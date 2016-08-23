# fengshui-api
Documentation and Samples for the Fengshui REST API. https://fengshui-api.com/

## Available calculators
| Id | Name | Function | Arguments
|----|------|----------------------|---------------
 1 | KUA number | findKuaNumber | $year, $month, $day, $gender
 2 | Chineese Sign of the Year | findChineseSignOfYear | $year, $month, $day
 3 | Chineese Sign of the Month | findChineseSignOfMonth | $year, $month, $day 
 4 | Chineese Sign of the Day | findChineseSignOfDay | $year, $month, $day
 5 | Chineese Sign of the Hour | findChineseSignOfHour | $hour
 6 | Astrological allies | findAstrologicalAllies | $year, $month, $day
 7 | Astrological enemy | findAstrologicalEnemy | $year, $month, $day
 8 | Secret friend | findSecretFriend | $year, $month, $day
 9 | Peach Blossom animal | findPeachBlossomAnimal | $year, $month, $day
10 | Love Compatibility | findLoveCompatibility | $year, $month, $day, $year2, $month2, $day2
11 | Bussiness compatibility | findBusinessCompatibility | $year, $month, $day, $year2, $month2, $day2
12 | Sign Compatibility | findSignCompatibility | $sign, $sign2
13 | Lucky dimension | getLuckyDimensions | $dimension
14 | Child gender | getChildGender | $age, $month
15 | Four Best Directions | getFourBestDirections | $kua, $gender
16 | Four Worst Directions | getFourWorstDirections | $kua, $gender
17 | Lo Shu | getOwnLoShu | $year, $month, $day
18 | Flying star | getFlyingStar | $period, $facing
19 | Eight mansions | getEightMansions | $facing

### Available options 
| name | description
|------|------------
kua | range (1-9)
gender | 0-boy, 1-girl
year | from 1890 to 2100
month | 1 - 12
day | 1 - 31
hour | 0 - 23
minutes | 0-59
dimension | in milimeters from 0
age | range ( 18-45 )
signs | [ 1 => 'Ox', 2 => 'Tiger', 3 => 'Rabbit', 4 => 'Dragon', 5 => 'Snake', 6 => 'Horse', 7 => 'Goat', 8 => 'Monkey', 9 => 'Rooster', 10 => 'Dog', 11 => 'Pig', 12 => 'Rat' ]
period | **in getFlyingStar function** [ 0 => '1864-1883', 1 => '1884-1903', 2 => '1904-1923', 3 => '1924-1943', 4 => '1944-1963', 5 => '1964-1983', 6 => '1984-2003', 7 => '2004-2023', 8 => '2024-2043' ]
facing | **in getFlyingStar function** [ 0 => 'N1', 1 => 'N2' , 2 => 'N3', 3 => 'NE1', 4 => 'NE2', 5 => 'NE3', 6 => 'E1', 7 => 'E2', 8 => 'E3', 9 => 'SE1', 10 => 'SE2', 11 => 'SE3', 12 => 'S1', 13 => 'S2', 14 => 'S3', 15 => 'SW1', 16 => 'SW2', 17 => 'SW3', 18 => 'W1', 19 => 'W2', 20 => 'W3', 21 => 'NW1', 22 => 'NW2', 23 => 'NW3' ]


## How to use this API in PHP:
```php

```

### Kua number

##### Number generated based on birth date and gender (Date range: 1890-2100), gender type: 0-male, 1-female
```php
  https://fengshui-api.com/api/v1/findKuaNumber?token=<your private server key>&year=2013&month=8&day=2&gender=0
``` 
##### reply:
```json
 {"status":"ok","result":6}
```

### Chinese Zodiac sign

##### Zodiak sign generated based on birth date (date range: 1890-2100)
```php
  https://fengshui-api.com/api/v1/findChineseSignOfYear?token=<your private server key>&year=2013&month=8&day=2&gender=1
```

##### reply:
```json
  {"status":"ok","result":"Snake"}
```

### Child gender

##### Child gender $age - the age of the child's mother, $month - Month To Get Pregnant (1-january)
```php
  https://fengshui-api.com/api/v1/getChildGender?token=<your private server key>&age=30&month=1
```

##### reply:
```json
  {"status":"ok","result":"boy"}
```

### Flying Star

##### Generated based on

Id | Year of construction | Id | Year of construction
------|------------|-----|-------
0 | 1864-1883 | 5 | 1964-1983
1 | 1884-1903 | 6 | 1984-2003
2 | 1904-1923 | 7 | 2004-2023
3 | 1924-1943 | 8 | 2024-2043
4 | 1944-1963

Id | Facing | Id | Facing | Id | Facing
---|--------|----|--------|----|-------
0 | N1 | 8 | E3 |  16  | SW2
1 | N2 | 9 | SE1 |  17  | SW3
2 | N3 | 10  | SE2 |  18  | W1
3 | NE1 | 11  | SE3 | 19  | W2
4 | NE2 | 12  | S1 |  20  | W3
5 | NE3 | 13  | S2 | 21  | NW1
6 | E1 | 14  | S3 | 22  | NW2
7 | E2 | 15  | SW1 | 23  | NW3

###### For example. If house was built in 2005 year ($period = 7) with windows facing the NE2 ($facing = 4).

```php
  https://fengshui-api.com/api/v1/getFlyingStar?token=<your private server key>&period=7&facing=4
```

##### reply:
```
  {"status":"ok","result":[6,3,9,1,7,4,8,5,2,7,4,1,5,2,8,3,9,6,2,8,5,9,6,3,4,1,7]}
```

#### Here is a graphical representation of the table:

![Flying Star example](https://fengshui-api.com/images/github/flying_star_example.png)
