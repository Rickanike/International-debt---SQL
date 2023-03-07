##  1. The World Bank's international debt data

<p>In this project the international debt data collected by the World Bank will be analyzed in order to extract valuable information out of it.

The dataset contains the following variables:</p>
<ul>
<li>Country name</li>
<li>Country code</li>
<li>Indicator name</li>
<li>Indicator code</li>
<li>Amount of debt in USD </li>
</ul>


```python
! pip install mysql-connector-python
! pip3 install pymysql
! pip3 install ipython-sql
! pip3 install mysqlclient

import pymysql
import pandas as pd

import mysql.connector 


```

    Requirement already satisfied: mysql-connector-python in c:\users\ricar\anaconda3\lib\site-packages (8.0.32)
    Requirement already satisfied: protobuf<=3.20.3,>=3.11.0 in c:\users\ricar\anaconda3\lib\site-packages (from mysql-connector-python) (3.20.3)
    Requirement already satisfied: pymysql in c:\users\ricar\anaconda3\lib\site-packages (1.0.2)
    Requirement already satisfied: ipython-sql in c:\users\ricar\anaconda3\lib\site-packages (0.5.0)
    Requirement already satisfied: ipython in c:\users\ricar\anaconda3\lib\site-packages (from ipython-sql) (7.31.1)
    Requirement already satisfied: prettytable in c:\users\ricar\anaconda3\lib\site-packages (from ipython-sql) (3.6.0)
    Requirement already satisfied: six in c:\users\ricar\anaconda3\lib\site-packages (from ipython-sql) (1.16.0)
    Requirement already satisfied: ipython-genutils in c:\users\ricar\anaconda3\lib\site-packages (from ipython-sql) (0.2.0)
    Requirement already satisfied: sqlparse in c:\users\ricar\anaconda3\lib\site-packages (from ipython-sql) (0.4.3)
    Requirement already satisfied: sqlalchemy>=2.0 in c:\users\ricar\anaconda3\lib\site-packages (from ipython-sql) (2.0.4)
    Requirement already satisfied: greenlet!=0.4.17 in c:\users\ricar\anaconda3\lib\site-packages (from sqlalchemy>=2.0->ipython-sql) (1.1.1)
    Requirement already satisfied: typing-extensions>=4.2.0 in c:\users\ricar\anaconda3\lib\site-packages (from sqlalchemy>=2.0->ipython-sql) (4.3.0)
    Requirement already satisfied: pygments in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (2.11.2)
    Requirement already satisfied: backcall in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (0.2.0)
    Requirement already satisfied: prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0 in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (3.0.20)
    Requirement already satisfied: pickleshare in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (0.7.5)
    Requirement already satisfied: decorator in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (5.1.1)
    Requirement already satisfied: matplotlib-inline in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (0.1.6)
    Requirement already satisfied: colorama in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (0.4.5)
    Requirement already satisfied: traitlets>=4.2 in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (5.1.1)
    Requirement already satisfied: jedi>=0.16 in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (0.18.1)
    Requirement already satisfied: setuptools>=18.5 in c:\users\ricar\anaconda3\lib\site-packages (from ipython->ipython-sql) (63.4.1)
    Requirement already satisfied: wcwidth in c:\users\ricar\anaconda3\lib\site-packages (from prettytable->ipython-sql) (0.2.5)
    Requirement already satisfied: parso<0.9.0,>=0.8.0 in c:\users\ricar\anaconda3\lib\site-packages (from jedi>=0.16->ipython->ipython-sql) (0.8.3)
    Requirement already satisfied: mysqlclient in c:\users\ricar\anaconda3\lib\site-packages (2.1.1)
    


```python
%load_ext sql

```


```python

%sql mysql+mysqldb://root:Welcome123@localhost/debt
```


```python
%sql SELECT * FROM international_debt;

```

     * mysql+mysqldb://root:***@localhost/debt
    2357 rows affected.
    




<table>
    <thead>
        <tr>
            <th>country_name</th>
            <th>country_code</th>
            <th>indicator_name</th>
            <th>indicator_code</th>
            <th>debt</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>72894453.7</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>53239440.1</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>61739336.9</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>49114729.4</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>39903620.1</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>39107845.0</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>23779724.3</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>13335820.0</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>100847181.9</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>72894453.7</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>53239440.1</td>
        </tr>
        <tr>
            <td>Afghanistan</td>
            <td>AFG</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>100847181.9</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>317194512.5</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>165602386.9</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>87884000.0</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>54250280.6</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>76050616.1</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>13847333.6</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>31030688.2</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>39445139.5</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>4542664.9</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>4618504.3</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>182197616.7</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>234321242.3</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>28101536.1</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>236447897.3</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>310371858.4</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>41948869.7</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>170018.4</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>2279989.2</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>120324.7</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>39615157.9</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>6822654.1</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>35769517.2</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>790248675.2</td>
        </tr>
        <tr>
            <td>Albania</td>
            <td>ALB</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>514185620.0</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>10320772.2</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>19031728.7</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>3220000.0</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>95188724.6</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>10320772.2</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>7680627.6</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>576463.5</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>13192.3</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>8094779.0</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>95188724.6</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>10320772.2</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>15775406.6</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>23129.8</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>576463.5</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>36322.1</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>171185188.1</td>
        </tr>
        <tr>
            <td>Algeria</td>
            <td>DZA</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>75420000.0</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>10924018093.1</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1798550445.5</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>8473824016.3</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>8838256901.1</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>1005053965.1</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1000000000.0</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>70000000.0</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>1125088719.9</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>1906771593.8</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>580902004.3</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>124688691.9</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>178989598.2</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>47038476.1</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>8598512708.2</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>9017246499.3</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1052092441.2</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>343444200.0</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>95556000.0</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>2468532919.9</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>1906771593.8</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>746458004.3</td>
        </tr>
        <tr>
            <td>Angola</td>
            <td>AGO</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>11067045628.1</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>426959175.6</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>275292981.1</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>128076000.0</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>68968314.7</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>174269846.7</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>24094832.0</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>65754000.0</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>1635012.0</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>196685.2</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>94331207.1</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>252689328.9</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>57171463.9</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>163299521.8</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>426959175.6</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>81266295.9</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1635012.0</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>65950685.2</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>845630723.8</td>
        </tr>
        <tr>
            <td>Armenia</td>
            <td>ARM</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>680696190.0</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1088458061.2</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>495732858.1</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>74183981.0</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>106369937.0</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>84748079.6</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>10085950.0</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>225022000.0</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>423613103.8</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>347550999.6</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>49574780.2</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>513623656.5</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>656158982.0</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>136577146.9</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>619993593.5</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>740907061.6</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>146663096.9</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>4110150.2</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>289000.0</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>427723254.0</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>347550999.6</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>274885780.2</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1513813661.4</td>
        </tr>
        <tr>
            <td>Azerbaijan</td>
            <td>AZE</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>466096813.9</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>9050557611.9</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>821146448.7</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>155543000.0</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>386702219.8</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>6141785637.5</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>309079773.4</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>3943983.7</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>1039564682.7</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>2908771974.4</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>356392675.3</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1426266902.5</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>9050557611.9</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>665472448.7</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>1683666.7</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>131000.0</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>5627650.4</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>131000.0</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2077014552.9</td>
        </tr>
        <tr>
            <td>Bangladesh</td>
            <td>BGD</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>645120000.0</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>2525227414.9</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1214489897.1</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>272640306.4</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>1487363278.5</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>2265336386.7</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>630234914.9</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>100750000.0</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>935058288.4</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>77099095.9</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>595438826.0</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>241493806.0</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>133026579.9</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>2082802104.5</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>2506830192.7</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>763261494.8</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>28912000.0</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>18397222.2</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>739000.0</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>963970288.4</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>18397222.2</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>178588095.9</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>4640037884.2</td>
        </tr>
        <tr>
            <td>Belarus</td>
            <td>BLR</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1593265491.3</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>53429527.6</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>53565437.1</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>4480000.0</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>23329498.4</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>3581448.7</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>3455608.4</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>26325100.0</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>33549000.0</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>1084000.0</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>29683326.5</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>49848078.9</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>10996828.7</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>53012824.9</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>53429527.6</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>14452437.1</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>26325100.0</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>34633000.0</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>105609924.9</td>
        </tr>
        <tr>
            <td>Belize</td>
            <td>BLZ</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>26272000.0</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>648444772.9</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>50293011.9</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>26014505.8</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>334698287.3</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>13208408.6</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>28675813.0</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>43999044.4</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>3565299.6</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>91631639.5</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>269747441.2</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>33519303.7</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>117646145.3</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>604445728.5</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>46727712.3</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>28675813.0</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>43999044.4</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>3565299.6</td>
        </tr>
        <tr>
            <td>Benin</td>
            <td>BEN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>146321958.3</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>149814565.8</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>201006184.1</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>189877869.8</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>95819437.4</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>184064524.8</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>5990246.6</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>11867672.1</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>8052276.3</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>17390420.5</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>42127456.3</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>8889383.0</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>207268290.3</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>137946893.7</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>192953907.8</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>5990246.6</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>11867672.1</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>8052276.3</td>
        </tr>
        <tr>
            <td>Bhutan</td>
            <td>BTN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>213258536.9</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1421491255.2</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>394855845.9</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>108075000.0</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>67814879.9</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>554128686.3</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>32609012.4</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>99122000.0</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>266701.5</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>16528896.5</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>62662.5</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>357721211.5</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>850833672.4</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>154977576.6</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>425536091.4</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1404962358.7</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>187586589.0</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>1076571.6</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>9594.4</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1343273.1</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>16528896.5</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>99194256.9</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1060650554.5</td>
        </tr>
        <tr>
            <td>Bolivia</td>
            <td>BOL</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>633771190.0</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>253819587.3</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>604620360.0</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>545519000.0</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>108704966.2</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>114375048.3</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>12605397.7</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>22306080.5</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>1625051.5</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>8958027.7</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>953443.5</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>290170946.5</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>139444539.0</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>43917467.3</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>398875912.7</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>253819587.3</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>56522865.0</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>31264108.2</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>2578495.0</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2112748020.9</td>
        </tr>
        <tr>
            <td>Bosnia and Herzegovina</td>
            <td>BIH</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1682608000.0</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>53337570.1</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>24028273.8</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>7903563.5</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>1316332.2</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>884447.5</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>125652344.5</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>52021237.9</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>23103826.3</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>133555908.0</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>53337570.1</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>23988273.8</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>4440000.0</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>40000.0</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>4440000.0</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>40000.0</td>
        </tr>
        <tr>
            <td>Botswana</td>
            <td>BWA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>137995908.0</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>4092388651.4</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>17001653109.2</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>10952236000.0</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>2097380010.6</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>1179125278.8</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>333237826.9</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1940858500.0</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>2550410063.2</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>6538835248.6</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>964149852.8</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>1846318920.2</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2514318741.6</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1949113519.8</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>706029298.9</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>4611698752.2</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>3128238798.6</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1039267125.8</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>35119003750.0</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>613421000.0</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>43598697498.6</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>964149852.8</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>5010149983.4</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>90041840304.1</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>BRA</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>41831444053.3</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>15032935.4</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1012039083.1</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>743516000.0</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>35764202.8</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>6012379.2</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>204322342.4</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>234043.4</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>87548.9</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>228993019.8</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>15032935.4</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>58100812.6</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>264757222.6</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>15032935.4</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>64113191.8</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>234043.4</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>204409891.3</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1883205166.2</td>
        </tr>
        <tr>
            <td>Bulgaria</td>
            <td>BGR</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1618213900.2</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>617436227.2</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>42083630.7</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>27371336.0</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>90915960.2</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>7382485.5</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>119510893.0</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>526520267.0</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>34701145.2</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>146882229.0</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>617436227.2</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>42083630.7</td>
        </tr>
        <tr>
            <td>Burkina Faso</td>
            <td>BFA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>146882229.0</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>64846467.3</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>2573479.6</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>10461498.5</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>42339024.4</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>520425.7</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>16115111.8</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>22507442.9</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>2053053.9</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>26576610.3</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>64846467.3</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>2573479.6</td>
        </tr>
        <tr>
            <td>Burundi</td>
            <td>BDI</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>26576610.3</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>109582071.9</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>21568390.7</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>11767654.3</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>37178444.8</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>4216236.3</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>15990666.7</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>27099862.5</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>10062127.0</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>39970124.9</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>45303764.6</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>7290027.4</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>51737779.2</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>82482209.4</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>11506263.7</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>15990666.7</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>27099862.5</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>10062127.0</td>
        </tr>
        <tr>
            <td>Cabo Verde</td>
            <td>CPV</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>67728445.9</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>642047150.8</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>183222625.4</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>93702000.0</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>223300273.6</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>476683829.4</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>63836683.2</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>72307001.8</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>165363321.4</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>25683942.2</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>295607275.4</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>642047150.8</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>89520625.4</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>775955981.3</td>
        </tr>
        <tr>
            <td>Cambodia</td>
            <td>KHM</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>480348705.9</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>18186662060.4</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>280795576.4</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>23235000.0</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>9999925153.3</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>17090544247.5</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>120877158.5</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>65222000.0</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>128608183.9</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>196167124.8</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>20590696.1</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>152095968.1</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>850036788.1</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>45124721.8</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>10152021121.4</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>17940581035.6</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>166001880.3</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>21809210.5</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>49913900.0</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>5746000.0</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>150417394.4</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>246081024.8</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>91558696.1</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>10404814960.2</td>
        </tr>
        <tr>
            <td>Cameroon</td>
            <td>CMR</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>102376444.4</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>53717612.9</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>2354220.8</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>8462062.9</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>19477551.6</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>860961.0</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2241813.8</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>34240061.3</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>1373259.8</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>10703876.7</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>53717612.9</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>2234220.8</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>400000.0</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>120000.0</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>400000.0</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>120000.0</td>
        </tr>
        <tr>
            <td>Central African Republic</td>
            <td>CAF</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>11103876.7</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>207090418.3</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>139946001.3</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>82357214.9</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>27987660.9</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>11882770.9</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>11033.6</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>4797.2</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>95738709.5</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>179102757.4</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>15590433.2</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>178095924.4</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>207090418.3</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>27473204.1</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>112468000.0</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>11033.6</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>112472797.2</td>
        </tr>
        <tr>
            <td>Chad</td>
            <td>TCD</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>178106958.0</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>15692563746.1</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>17866548651.4</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>14142718751.6</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>6532446441.9</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>514898407.1</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>9834677000.0</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>1224249000.0</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>4046243298.5</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>3777050273.3</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>969933090.0</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2615723714.1</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>3079501272.1</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>858406974.8</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>9148170156.0</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>3079501272.1</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1373305381.9</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>796544167.4</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>334012200.7</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>156342427.9</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>14677464465.9</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>4111062474.0</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>2350524517.9</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>96218620835.7</td>
        </tr>
        <tr>
            <td>China</td>
            <td>CHN</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>72392986213.8</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>704314557.6</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>4564574602.1</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>1424280000.0</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>447557894.1</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>110671664.3</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>122715407.2</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>4398582816.7</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>2362344669.4</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>1129332984.3</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>13429800.0</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>176027787.7</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>1100907553.6</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>580213093.3</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>479206737.8</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1548465447.7</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>690884757.6</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>601922145.0</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>5527915801.0</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>13429800.0</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>2538372457.1</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>11985674438.7</td>
        </tr>
        <tr>
            <td>Colombia</td>
            <td>COL</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>4909293190.0</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>13460035.4</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>937189.9</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>2610216.0</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>8492726.4</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>782831.5</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2182053.1</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>4967309.0</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>154358.4</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>4792269.1</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>13460035.4</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>937189.9</td>
        </tr>
        <tr>
            <td>Comoros</td>
            <td>COM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>4792269.1</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>370323229.6</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>116207399.2</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>116452329.4</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>103263632.0</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>62260653.1</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>278750.0</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>143105462.0</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>267059597.6</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>53946746.1</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>259557791.4</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>370323229.6</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>116207399.2</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>278750.0</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Congo, Dem. Rep.</td>
            <td>COD</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>259836541.4</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>247432137.7</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>33115657.6</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>186071498.1</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>150347308.2</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>19522109.8</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>8736000.0</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>21696428.5</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>189000.0</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>18114469.0</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>97084829.5</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>4668547.8</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>204185967.1</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>247432137.7</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>24190657.6</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>21696428.5</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>8925000.0</td>
        </tr>
        <tr>
            <td>Congo, Rep.</td>
            <td>COG</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>225882395.6</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>600552336.8</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1031562783.4</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>491033000.0</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>34085176.1</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>105969275.9</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>10709783.4</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>361312000.0</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>351141926.7</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>1234500.0</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>59937000.0</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>272808260.7</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>493348560.9</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>108571000.0</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>306893436.8</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>599317836.8</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>119280783.4</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>351141926.7</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>1234500.0</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>421249000.0</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1776491747.9</td>
        </tr>
        <tr>
            <td>Costa Rica</td>
            <td>CRI</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1118456384.4</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1081936422.8</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>422427447.9</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>30540339.7</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>478283000.5</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>526901028.0</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>73124399.9</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>126548133.3</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>282160778.3</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>84629406.5</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>555035394.8</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>36573930.0</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>562912407.0</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1081936422.8</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>109698329.9</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>11333333.3</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>28000.0</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>137881466.6</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>282188778.3</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>979241934.4</td>
        </tr>
        <tr>
            <td>Cote d&#x27;Ivoire</td>
            <td>CIV</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>278448060.8</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>176522478.2</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>54325937.5</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>48803279.1</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>85687012.1</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>44878881.9</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>127000.0</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>11000.0</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>34254909.2</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>90835466.1</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>9436055.6</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>83058188.3</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>176522478.2</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>54314937.5</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>127000.0</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>11000.0</td>
        </tr>
        <tr>
            <td>Djibouti</td>
            <td>DJI</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>83185188.3</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>17673239.0</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>6947369.4</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>8487067.1</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>1092575.0</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>1693891.5</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>97108.5</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>1706962.9</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>1142907.2</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>288740.8</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>11130355.8</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>16580664.0</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>3120737.1</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>19617422.9</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>17673239.0</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>4814628.6</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>536719.6</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>137037.1</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1776735.3</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>2132740.8</td>
        </tr>
        <tr>
            <td>Dominica</td>
            <td>DMA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>21394158.2</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>643781535.5</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1365524193.4</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>424284000.0</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>214014574.6</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>311336450.8</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>43812226.9</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>766308000.0</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>313591688.9</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>136346421.2</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>39744531.5</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>63295059.0</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>254728306.1</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>186149762.4</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>91151435.0</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>468742880.7</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>497486213.2</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>134963661.9</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>9497666.6</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>9948901.1</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>224000.0</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>323089355.5</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>146295322.3</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>806276531.5</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1978111141.2</td>
        </tr>
        <tr>
            <td>Dominican Republic</td>
            <td>DOM</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1186278905.0</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>819756142.2</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1902464851.8</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>222441000.0</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>1177917742.6</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>415778474.8</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>424453624.8</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>360282500.0</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>809837000.0</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>79394343.7</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>60256258.1</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>207314486.5</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>578894793.9</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>343721409.3</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>237657740.5</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1756812536.5</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>759499884.1</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>662111365.3</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>122807000.0</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>761000.0</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>562483843.7</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>60256258.1</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>1017912486.5</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>3623731570.2</td>
        </tr>
        <tr>
            <td>Ecuador</td>
            <td>ECU</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1304435190.0</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>9552207423.5</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1480967451.0</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>3477000.0</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>6949184320.5</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>7275502144.4</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>462561367.0</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>607496000.0</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>222817364.8</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>196463721.6</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>85717906.5</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2424904078.0</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>2080241557.5</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>321643387.3</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>9374088398.5</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>9355743701.9</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>784204754.3</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>546016.3</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>71790.2</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>223363381.1</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>196463721.6</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>693285696.7</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>9692114176.9</td>
        </tr>
        <tr>
            <td>Egypt, Arab Rep.</td>
            <td>EGY</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>94662397.3</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>245967023.2</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>690320052.7</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>163296000.0</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>46180727.2</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>16377537.9</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>10447436.1</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1259866714.3</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>393550000.0</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>11407489.1</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>72460052.2</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>11143690.6</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>298939687.1</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>157129433.1</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>111128086.3</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>345120414.3</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>173506971.0</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>121575522.4</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>555864.6</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>754839.7</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1271830068.0</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>72460052.2</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>405448530.3</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2574548482.3</td>
        </tr>
        <tr>
            <td>El Salvador</td>
            <td>SLV</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>957598000.0</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>7203213.6</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>5851311.7</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>15627602.4</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>2678802.6</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>1556112.1</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>15482475.4</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>4524411.0</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>4124899.0</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>31110077.8</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>7203213.6</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>5681011.1</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>170300.6</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>170300.6</td>
        </tr>
        <tr>
            <td>Eritrea</td>
            <td>ERI</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>31110077.8</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>106108147.6</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>12654109.2</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>21586421.3</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>54462529.7</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>5511319.0</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>1801378.1</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>18130218.8</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>51645617.9</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>5341412.1</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>39716640.1</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>106108147.6</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>10852731.1</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>1801378.1</td>
        </tr>
        <tr>
            <td>Eswatini</td>
            <td>SWZ</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>39716640.1</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>2681493007.3</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>702459842.2</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>510741366.9</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>1142444763.3</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>331367061.4</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>65998000.0</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>294411928.4</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>127663171.3</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>120237813.8</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>171590722.7</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1344105921.6</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>95255967.0</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>682332089.6</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>2486550684.9</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>426623028.4</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>212179959.6</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>67279151.1</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>89601000.0</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>506591888.0</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>194942322.4</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>275836813.8</td>
        </tr>
        <tr>
            <td>Ethiopia</td>
            <td>ETH</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1188923977.6</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>207893813.6</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>66510192.6</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>27910526.5</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>12000.0</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>37382876.6</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>3902886.7</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>6175526.5</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>13250000.0</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>9082442.6</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>62607305.9</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>8473000.0</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>46465319.2</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>66510192.6</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>14648526.5</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>13250000.0</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>46532508.5</td>
        </tr>
        <tr>
            <td>Fiji</td>
            <td>FJI</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>67189.3</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>519921205.7</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>209330192.9</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>114697076.0</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>354919707.0</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>33263802.5</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>144272000.0</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>153982580.5</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>18711238.7</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>13403376.8</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>62404132.3</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>146290260.0</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>18155013.6</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>177101208.3</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>501209967.0</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>51418816.1</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>2233200.0</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>236000.0</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>156215780.5</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>18711238.7</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>157911376.8</td>
        </tr>
        <tr>
            <td>Gabon</td>
            <td>GAB</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>333316988.8</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>89552885.9</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>8397638.2</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>13014909.1</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>21371548.3</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>2686367.0</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>974231.4</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>3597.9</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>33231516.7</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>68181337.6</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>5707673.3</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>46246425.8</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>89552885.9</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>8394040.3</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>974231.4</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>3597.9</td>
        </tr>
        <tr>
            <td>Gambia, The</td>
            <td>GMB</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>47220657.2</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>775345350.5</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>3087990080.3</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>536500000.0</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>63831412.1</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>110677830.3</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>2435342284.4</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>51374000.0</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>14240741.3</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>3992133.9</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>1478736.9</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>144062401.5</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>660675386.3</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>771353216.6</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>2498637343.4</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>14240741.3</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>3992133.9</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>52852736.9</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1552116953.6</td>
        </tr>
        <tr>
            <td>Georgia</td>
            <td>GEO</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1329982398.7</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1508869861.5</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>624681303.4</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>6328000.0</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>865892038.7</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>1163413713.8</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>105007672.0</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>336874000.0</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>583268468.8</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>180680823.3</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>92690304.9</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>130202003.1</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>164459939.3</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>57076217.8</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>996094041.8</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1327873653.1</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>162083889.8</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>109966322.9</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>315385.1</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>26705108.7</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>693234791.7</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>180996208.4</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>456269413.6</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1689328833.5</td>
        </tr>
        <tr>
            <td>Ghana</td>
            <td>GHA</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>41250138.3</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>15665767.8</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>11639110.2</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>23225424.8</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>3290655.4</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>8983520.0</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>7073000.0</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>13740888.8</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>18024713.5</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>5302112.4</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>25379999.0</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>41250138.3</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>8592767.8</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>8983520.0</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>7073000.0</td>
        </tr>
        <tr>
            <td>Grenada</td>
            <td>GRD</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>34363519.0</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>137925963.9</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>563718062.4</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>377836407.3</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>41738434.7</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>56408511.8</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>8721281.3</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>49440000.0</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>218565.2</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>8311149.0</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>42861.1</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>339822253.6</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>73206303.1</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>127677512.7</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>381560688.3</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>129614814.9</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>136398794.0</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>218565.2</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>8311149.0</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>49482861.1</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2911981987.8</td>
        </tr>
        <tr>
            <td>Guatemala</td>
            <td>GTM</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>2530202734.3</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>175441526.2</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>11444027.9</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>8832105.1</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>61782399.4</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>3723822.7</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>644000.0</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>29819676.8</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>113659126.8</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>7076205.2</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>38651781.9</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>175441526.2</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>10800027.9</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>644000.0</td>
        </tr>
        <tr>
            <td>Guinea</td>
            <td>GIN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>38651781.9</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>48265990.2</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1462857.5</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>70371.9</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>24800.0</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>6713257.2</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>48265990.2</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>1438057.5</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>6783629.1</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>48265990.2</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1462857.5</td>
        </tr>
        <tr>
            <td>Guinea-Bissau</td>
            <td>GNB</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>6783629.1</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>93057520.1</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>27615299.5</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>8189000.0</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>21758525.7</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>35584684.1</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>4885618.3</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>1153800.0</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>1078000.0</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>34651806.5</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>57472836.0</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>13462681.2</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>56410332.2</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>93057520.1</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>18348299.5</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1153800.0</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>1078000.0</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>108264665.5</td>
        </tr>
        <tr>
            <td>Guyana</td>
            <td>GUY</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>50700533.3</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>25668662.8</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>12695243.1</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>51356369.6</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>1597000.0</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>10474000.0</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>10087968.8</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>24071662.8</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>2221243.1</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>61444338.4</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>25668662.8</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>12695243.1</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>61444338.4</td>
        </tr>
        <tr>
            <td>Haiti</td>
            <td>HTI</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>271661829.8</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>245990147.3</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>36010000.0</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>35890751.9</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>91251459.7</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>31044538.5</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>81936000.0</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>17892790.4</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>11102903.5</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>1489545.0</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>148225048.7</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>169307466.6</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>95482063.8</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>184115800.6</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>260558926.3</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>126526602.3</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>45052.6</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>28000.0</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>17937843.0</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>11102903.5</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>83453545.0</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>412459703.3</td>
        </tr>
        <tr>
            <td>Honduras</td>
            <td>HND</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>210406059.7</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>34531188113.2</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>7269408633.8</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>1174413339.7</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>6273480947.8</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>16882903064.4</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>2351375435.8</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>329916650.2</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>1310931559.6</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>2129231057.8</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>909245034.7</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>432970941.8</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>4884095623.3</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>16375327102.5</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>1755479051.6</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>11157576571.1</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>33258230166.9</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>4106854487.4</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>426977610.9</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>268947911.6</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>244238305.3</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>2886125318.9</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>1178192946.3</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>1988140806.7</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>20483289208.0</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>IDX</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>6439587318.0</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>11005547326.2</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>11419475865.8</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>9111461000.0</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>2451995834.5</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>5588550763.4</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>455965157.6</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1133333333.3</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>459247709.8</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>3483945853.1</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>83527746.3</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>530195104.4</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>4545609909.9</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>5333468816.5</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>862200894.0</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>6997605744.4</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>10922019579.9</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1318166051.6</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>1553450.0</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>406000.0</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>4618832636.4</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>83527746.3</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>989848814.2</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>31923507000.8</td>
        </tr>
        <tr>
            <td>India</td>
            <td>IND</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>20307068620.0</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>4177287375.8</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>10190097793.8</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>3770921966.7</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>3233436193.9</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>2289402723.3</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>476814537.9</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>4114167404.8</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>5232651353.5</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>977304350.0</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>455534555.3</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>90231831.1</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2469145824.7</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1214274597.2</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>561775658.4</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>5702582018.6</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>3503677320.5</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1038590196.3</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>1478184070.4</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>218075500.0</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>57702446.2</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>6569655825.2</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>673610055.3</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>5380585630.8</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>30916112653.8</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>IDN</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>18643874810.0</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>32761505.6</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>15907227.6</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>18506048.0</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>11333050.3</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>9025208.2</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>32761505.6</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>374715.9</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>78354060.8</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>4199461.4</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>96860108.8</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>15532511.7</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>9025208.2</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>32761505.6</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>374715.9</td>
        </tr>
        <tr>
            <td>Iran, Islamic Rep.</td>
            <td>IRN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>105885317.0</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>188717385.7</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>661568432.2</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>104466000.0</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>93733672.1</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>112848973.6</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>19718160.9</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>100473736.8</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>470652000.0</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>45845850.2</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>2086139.2</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>174427648.0</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>75868412.1</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>64135132.1</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>268161320.1</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>188717385.7</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>83853293.0</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>1268714.3</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>511000.0</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>147588301.3</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>473249139.2</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>559597431.4</td>
        </tr>
        <tr>
            <td>Jamaica</td>
            <td>JAM</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>143847810.0</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>473703814.3</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>533968850.8</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>75949000.0</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>230204467.2</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>175484307.3</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>62136103.7</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1029000000.0</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>306023000.0</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>3680522.3</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>3441455.0</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>4228342.9</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>270498715.5</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>294778052.0</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>84738685.9</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>500703182.7</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>470262359.3</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>146874789.6</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>11580964.2</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>893718.3</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1044261486.5</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>3441455.0</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>311145061.2</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1990343479.2</td>
        </tr>
        <tr>
            <td>Jordan</td>
            <td>JOR</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>445378810.0</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>874231247.0</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>5333500397.9</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>4552173000.0</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>44784496.7</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>254112169.3</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>49233512.4</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>564251000.0</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>1079948889.7</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>620119077.7</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>167842885.5</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1124733386.4</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>874231247.0</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>217076397.9</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>564251000.0</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>27482093686.4</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>KAZ</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>26357360300.0</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>4266494939.7</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>819196742.6</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>26876362.7</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>515101268.1</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>1582905042.0</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>342056817.0</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>500000000.0</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>184060000.0</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>897058411.6</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>842857183.4</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>94818544.2</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>391340889.9</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1840732714.3</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>167570018.7</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>906442158.0</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>3423637756.3</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>509626835.7</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>53632026.6</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>3815000.0</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1450690438.2</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>842857183.4</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>282693544.2</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2517537554.7</td>
        </tr>
        <tr>
            <td>Kenya</td>
            <td>KEN</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>160404958.5</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>115599658.5</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>42610586.9</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>32562000.0</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>5173195.2</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>29959141.9</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>1704127.3</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>2609476.0</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>699191.9</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>33590154.6</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>85640516.6</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>7645267.7</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>38763349.8</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>115599658.5</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>9349395.0</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>2609476.0</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>699191.9</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>232317825.8</td>
        </tr>
        <tr>
            <td>Kosovo</td>
            <td>XKX</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>190945000.0</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>837442293.4</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>145952992.6</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>63535000.0</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>62213250.6</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>153027414.4</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>43802082.9</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>75278037.2</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>684414879.0</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>38615909.7</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>137491287.8</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>837442293.4</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>82417992.6</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>816419045.1</td>
        </tr>
        <tr>
            <td>Kyrgyz Republic</td>
            <td>KGZ</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>678927757.3</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1135545159.8</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>418497462.5</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>183013000.0</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>346861942.2</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>966004791.1</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>134508386.6</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>203368516.9</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>67466781.3</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>25954663.4</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>25145870.4</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>5213357.1</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>80684114.6</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>131394498.3</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>26353937.5</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>427546056.8</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1097399289.4</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>160862324.1</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>8488563.0</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>13000000.0</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>1942000.0</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>237811743.3</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>38145870.4</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>74622138.4</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1605959990.1</td>
        </tr>
        <tr>
            <td>Lao PDR</td>
            <td>LAO</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>940602190.0</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>2704841.4</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>40160766261.6</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>7085064805.2</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>766272000.0</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>12944703036.6</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>23333956388.4</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>3029826352.3</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1203368516.9</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>662460781.3</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>2636028272.9</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>2621897864.6</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>917218236.6</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>4084275524.2</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>13940020962.1</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>1396668176.3</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>17028978560.8</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>37273977350.5</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>4426494528.6</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>647337642.1</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>264891046.5</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>312619258.7</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>4486734431.9</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>2886788911.1</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>1892298276.6</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>25197029299.4</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>LDC</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>3681316306.7</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>569983871.3</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>2131942998.7</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>413768000.0</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>137130312.1</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>129913451.7</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>16970779.5</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>2653766481.1</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>1649553000.0</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>33485786.7</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>17404140.4</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>2469762.0</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>167638089.7</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>419104358.2</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>49181457.2</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>304768401.8</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>549017809.9</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>66152236.7</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>3561921.0</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>2687252267.8</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>20966061.4</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>1652022762.0</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>9506919669.6</td>
        </tr>
        <tr>
            <td>Lebanon</td>
            <td>LBN</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>6514899000.0</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>80548591.6</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>19145345.9</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>12806231.5</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>13239867.2</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>157326.4</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>80353.1</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>32459403.7</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>67308724.4</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>16360151.4</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>45265635.2</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>80548591.6</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>19064992.8</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>157326.4</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>80353.1</td>
        </tr>
        <tr>
            <td>Lesotho</td>
            <td>LSO</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>45422961.6</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>150961031.2</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>9659434.0</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>903000.0</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>602095.8</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>33122214.9</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>2971664.1</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>7383619.4</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>117838816.3</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>5784769.9</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>7985715.2</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>150961031.2</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>8756434.0</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>15621477.1</td>
        </tr>
        <tr>
            <td>Liberia</td>
            <td>LBR</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>7635761.9</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>297334137.6</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>220478984.1</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>107314000.0</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>70570550.3</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>101396578.4</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>14127618.6</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>69976756.4</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>47599336.7</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>15758935.3</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>13087380.5</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>185952867.2</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>180178623.9</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>15973228.6</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>256523417.5</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>281575202.3</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>30100847.2</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>66332.2</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>47665668.9</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>15758935.3</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>83064136.9</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>875846538.5</td>
        </tr>
        <tr>
            <td>Macedonia, FYR</td>
            <td>MKD</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>571657452.1</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>446922027.4</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>25558623.1</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>120000.0</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>34102362.9</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>201529156.1</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>3611119.1</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>11734526.6</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>3043823.4</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>60669367.3</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>240358091.6</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>18687622.3</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>94771730.2</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>441887247.7</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>22298741.4</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>576061.8</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>5034779.7</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>96058.3</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>12310588.4</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>5034779.7</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>3139881.7</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>107783128.8</td>
        </tr>
        <tr>
            <td>Madagascar</td>
            <td>MDG</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>700810.2</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>132165820.5</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>19391773.5</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>21762541.7</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>26559943.3</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>7850229.4</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>35659831.4</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>105605877.2</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>11541544.1</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>57422373.1</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>132165820.5</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>19391773.5</td>
        </tr>
        <tr>
            <td>Malawi</td>
            <td>MWI</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>57422373.1</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>324159093.3</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>50631355.7</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>8609000.0</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>48054924.5</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>171056385.2</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>17789090.5</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>17500000.0</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>13237105.9</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>628108.3</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>17896143.5</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>58337708.1</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>6105156.9</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>65951068.0</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>229394093.3</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>23894247.4</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>13237105.9</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>18128108.3</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>124022584.1</td>
        </tr>
        <tr>
            <td>Maldives</td>
            <td>MDV</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>44834410.2</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>602617562.3</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>49454533.0</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>80562273.4</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>174563540.6</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>14961901.1</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>68120.2</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>135472245.9</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>428054021.7</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>34492631.9</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>216034519.3</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>602617562.3</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>49454533.0</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>68120.2</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Mali</td>
            <td>MLI</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>216102639.5</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>587173043.9</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>92943151.5</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>197041185.1</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>262893890.2</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>39896318.9</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>184408220.2</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>324279153.7</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>53046832.6</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>381449405.3</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>587173043.9</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>92943151.5</td>
        </tr>
        <tr>
            <td>Mauritania</td>
            <td>MRT</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>381449405.3</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>58239434.1</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>439563477.8</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>415091000.0</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>113174983.3</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>43276477.1</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>13702507.5</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>5462211.9</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>170300.6</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>74568335.5</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>14962957.0</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>10599669.7</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>187743318.8</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>58239434.1</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>24302177.2</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>5462211.9</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>170300.6</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1757803962.2</td>
        </tr>
        <tr>
            <td>Mauritius</td>
            <td>MUS</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1564598431.5</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>647628548.1</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>19267966623.4</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>5466172888.2</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>382457219.1</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>10959800.0</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>59839853.4</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>17109552312.5</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>12310714652.8</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>1462493107.5</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>751107387.1</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>864181883.5</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>636668748.1</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>610319408.9</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1246639102.6</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>647628548.1</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>670159262.3</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>60481214.4</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>69812433.0</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>18632526634.4</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>13131634472.9</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>25218503927.0</td>
        </tr>
        <tr>
            <td>Mexico</td>
            <td>MEX</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>5339338190.0</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>128096689.4</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>442210632.8</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>130618875.2</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>107393000.0</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>52456210.6</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>31959827.1</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>3292727.3</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>551019.7</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>55167.8</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>135842865.5</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>410250805.7</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>19877980.1</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>188299076.1</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>442210632.8</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>23170707.4</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>551019.7</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>55167.8</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>769232867.0</td>
        </tr>
        <tr>
            <td>Moldova</td>
            <td>MDA</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>580382771.2</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>337260763.6</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>877048982.5</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>596718000.0</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>52159543.5</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>122040716.9</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>23580386.5</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>203124000.0</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>80000000.0</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>1259265.0</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>17811674.5</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>75937145.9</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>213960781.7</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>35814921.5</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>336001498.6</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>59395308.0</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>80000000.0</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>1259265.0</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>220935674.5</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>3296470965.6</td>
        </tr>
        <tr>
            <td>Mongolia</td>
            <td>MNG</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>3088374276.2</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>251048938.5</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>104386053.0</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>3780193.6</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>127450152.9</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>159653202.4</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>20505157.3</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>335804000.0</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>61972628.2</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>81065238.7</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>7085884.0</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>77948064.8</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>91395736.1</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>10777144.6</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>205398217.7</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>251048938.5</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>31282301.9</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>6288038.9</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>265045.3</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>423157277.6</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>69323557.5</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>650720957.9</td>
        </tr>
        <tr>
            <td>Montenegro</td>
            <td>MNE</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>22165462.6</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1971794584.4</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>988479361.5</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>153363000.0</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>742287180.6</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>381225311.4</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>147741097.6</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>270530500.0</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>323617953.1</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>78436344.8</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>115518403.2</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>1381649282.3</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1512132928.2</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>296913749.4</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>2123936462.9</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1893358239.6</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>444654847.0</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>10291875.1</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>4412611.3</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>333909828.2</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>78436344.8</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>390461514.5</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>5153430846.8</td>
        </tr>
        <tr>
            <td>Morocco</td>
            <td>MAR</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>2695584555.7</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>749659443.7</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>184653722.7</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>307444585.4</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>428319700.7</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>89226721.5</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>53592000.0</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>200988925.7</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>46219486.9</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>7893817.2</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>91225626.1</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>275120256.1</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>33911201.5</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>398670211.5</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>703439956.8</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>123137923.0</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>2270758.9</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>29982.5</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>203259684.6</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>46219486.9</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>61515799.7</td>
        </tr>
        <tr>
            <td>Mozambique</td>
            <td>MOZ</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>601929896.1</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1246429044.3</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>240557887.7</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>86000.0</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>519713545.7</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>704626596.3</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>217742156.0</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>30569845.2</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>541802448.0</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>21203731.7</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>550283390.9</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1246429044.3</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>238945887.7</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>1526000.0</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>1526000.0</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>559727724.2</td>
        </tr>
        <tr>
            <td>Myanmar</td>
            <td>MMR</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>9444333.3</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>854955604.0</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>63814504.0</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>3143000.0</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>48512381.5</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>211256468.1</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>8120651.8</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>163747512.9</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>643699135.9</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>52550852.2</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>212259894.4</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>854955604.0</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>60671504.0</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>220142894.4</td>
        </tr>
        <tr>
            <td>Nepal</td>
            <td>NPL</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>7883000.0</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>710353661.5</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>281975237.4</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>165274000.0</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>33414678.5</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>91410630.2</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>9117269.5</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>105260.3</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>2335037.1</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>69559.4</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>181115898.0</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>612866514.2</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>107100470.6</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>214530576.5</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>704277144.4</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>116217740.1</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>1739460.0</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>3741480.0</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>413937.9</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1844720.3</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>6076517.1</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>483497.3</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1185575296.8</td>
        </tr>
        <tr>
            <td>Nicaragua</td>
            <td>NIC</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>969200000.0</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>613393210.2</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>58798606.4</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>38815599.9</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>150675402.1</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>20553332.6</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>115132364.5</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>462717808.1</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>38245273.8</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>153947964.4</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>613393210.2</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>58798606.4</td>
        </tr>
        <tr>
            <td>Niger</td>
            <td>NER</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>153947964.4</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1642510515.7</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1174953817.6</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>601884000.0</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>86761615.4</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>197807330.6</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>69169718.3</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>380622000.0</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>297246686.6</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1444703185.1</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>123278099.3</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>384008302.0</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1642510515.7</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>192447817.6</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>380622000.0</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2957693969.5</td>
        </tr>
        <tr>
            <td>Nigeria</td>
            <td>NGA</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>2573685667.5</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>5301166769.9</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>2018025408.3</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>266062000.0</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>2175483884.5</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>3281555124.0</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>719897921.2</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>2000000000.0</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>466998000.0</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>968637742.9</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>46666666.7</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>89037000.0</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>1578651453.9</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1972944979.2</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>475235487.1</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>3754135338.4</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>5254500103.2</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1195133408.3</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>53000000.0</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>795000.0</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>3021637742.9</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>46666666.7</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>556830000.0</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>8336013891.3</td>
        </tr>
        <tr>
            <td>Pakistan</td>
            <td>PAK</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1560240810.0</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>601895761.5</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>551188611.7</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>474262000.0</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>30768505.2</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>272745704.4</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>17727088.6</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>5617161.4</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>27030914.8</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>24544600.8</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>78345326.0</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>302119142.3</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>34654922.3</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>109113831.2</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>574864846.7</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>52382010.9</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>5617161.4</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>27030914.8</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>24544600.8</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2842193842.5</td>
        </tr>
        <tr>
            <td>Papua New Guinea</td>
            <td>PNG</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>2727462849.9</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>477257251.5</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>393918250.5</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>181087000.0</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>58314162.7</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>132431540.4</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>5158922.3</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>150500000.0</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>19355000.0</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>411000.0</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>207662030.9</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>344825711.1</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>56761328.2</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>265976193.6</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>477257251.5</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>61920250.5</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>19355000.0</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>150911000.0</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1528508573.6</td>
        </tr>
        <tr>
            <td>Paraguay</td>
            <td>PRY</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1243177380.0</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1701637273.3</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>2592895979.3</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>1618289000.0</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>114574694.7</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>123873090.2</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>20175359.1</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>395741000.0</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>834211575.0</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>553634090.0</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1577764183.1</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>120220045.2</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>668208784.7</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1701637273.3</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>140395404.3</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>395741000.0</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>834211575.0</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>5881259974.7</td>
        </tr>
        <tr>
            <td>Peru</td>
            <td>PER</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>4817310190.0</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1599376586.3</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1835490244.3</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>690769000.0</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>670475417.9</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>544148527.8</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>104237992.9</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>903941000.0</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>767514405.9</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>215119588.1</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>162804936.2</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>16718030.9</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>739056427.3</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>851399752.4</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>254559486.9</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1409531845.2</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1395548280.2</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>358797479.8</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>50941024.5</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>41023369.9</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>1691327.7</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1170001612.6</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>203828306.1</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>785923764.5</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>6479170917.7</td>
        </tr>
        <tr>
            <td>Philippines</td>
            <td>PHL</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>3899637459.9</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1381014186.3</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>2906875294.6</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>1790450000.0</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>46961486.3</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>115066917.8</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>8014478.4</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1798950000.0</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>917027107.3</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>68977772.6</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>1001655.4</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>7130421.7</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>1798305095.8</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1264945613.1</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>184253287.2</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1845266582.1</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1380012530.9</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>192267765.6</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1867927772.6</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>1001655.4</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>924157529.0</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>14013783350.4</td>
        </tr>
        <tr>
            <td>Romania</td>
            <td>ROU</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>10300588995.7</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>33043274.4</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>13929825315.6</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>7568679036.4</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>69924222.2</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>11030000.0</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1500000000.0</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>2113157602.7</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>22077398848.1</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>4228747124.8</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>141669500.0</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>33043274.4</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>8201415.9</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>211593722.2</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>33043274.4</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>19231415.9</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>614288.3</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>10135.8</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>23578013136.4</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>6341914863.3</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>66589761833.5</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>RUS</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>42800154974.9</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>327248280.2</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>54069081.6</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>8604526.0</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>69086251.9</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>7310975.7</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>26500000.0</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>31090382.5</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>258162028.3</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>20258105.9</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>39694908.5</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>327248280.2</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>27569081.6</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>26500000.0</td>
        </tr>
        <tr>
            <td>Rwanda</td>
            <td>RWA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>39694908.5</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>10815581.1</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>5117819.0</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>11727921.8</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>3362614.4</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>2965245.0</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>9987486.6</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>7452966.7</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>2152574.0</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>21715408.4</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>10815581.1</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>5117819.0</td>
        </tr>
        <tr>
            <td>Samoa</td>
            <td>WSM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>21715408.4</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>10636848.5</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1354432.7</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>522448.7</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>1918.9</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>802594.2</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2418947.6</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>10634929.6</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>551838.5</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>2941396.3</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>10636848.5</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1354432.7</td>
        </tr>
        <tr>
            <td>Sao Tome and Principe</td>
            <td>STP</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2941396.3</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1661790101.6</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>266493300.4</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>132241030.2</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>548648509.1</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>62856549.3</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>140824000.0</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>98043761.1</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>61799481.2</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>5561154.1</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>170437929.1</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>886747852.7</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>53740046.6</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>302678959.3</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1435396361.8</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>116596595.9</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>43999835.6</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>164594258.6</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>3511550.4</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>142043596.7</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>226393739.8</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>149896704.5</td>
        </tr>
        <tr>
            <td>Senegal</td>
            <td>SEN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>444722556.0</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1390127107.3</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1087126443.3</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>589206331.6</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>328727524.6</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>703434606.4</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>156469393.1</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>238124000.0</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>6515073.8</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>2967178.9</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>621929.8</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>715223963.7</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>623050701.0</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>92872223.3</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1043951488.3</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1326485307.4</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>249341616.4</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>27982786.4</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>60674621.0</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>9832565.5</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>34497860.2</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>63641799.9</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>248578495.3</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>3409673950.0</td>
        </tr>
        <tr>
            <td>Serbia</td>
            <td>SRB</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>2331224601.5</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>98339852.8</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>7862712.9</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>8755657.7</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>32566565.0</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>2736397.7</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>24144262.8</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>65773287.8</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>5126315.2</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>32899920.5</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>98339852.8</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>7862712.9</td>
        </tr>
        <tr>
            <td>Sierra Leone</td>
            <td>SLE</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>32899920.5</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>8645249.9</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>5410035.3</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>3721000.0</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>1207375.0</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>284000.0</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>3952828.9</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>8645249.9</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>1405035.3</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>5160203.9</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>8645249.9</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1689035.3</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>30749703.9</td>
        </tr>
        <tr>
            <td>Solomon Islands</td>
            <td>SLB</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>25589500.0</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>2456971.6</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>4429352.4</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>8301771.4</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>925000.0</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>24683262.9</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>2456971.6</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>3504352.4</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>32985034.3</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>2456971.6</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>4429352.4</td>
        </tr>
        <tr>
            <td>Somalia</td>
            <td>SOM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>32985034.3</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>714762584.5</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>4872276053.4</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>957111168.5</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>2000000000.0</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>3766186000.0</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>398510262.9</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>44117700.0</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>65728818.1</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>346393763.9</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>251984484.5</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>82716066.8</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>346393763.9</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>251984484.5</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>82716066.8</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>43837666.7</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>534000.0</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>2442347929.6</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>44117700.0</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>3832448818.1</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>9474257551.9</td>
        </tr>
        <tr>
            <td>South Africa</td>
            <td>ZAF</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>6685515858.4</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>29306216064.7</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>15931560388.1</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>9813113000.0</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>6437804448.1</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>17269114040.9</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>2004917449.3</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>4883333333.3</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>1515738709.8</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>5004801917.3</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>219553713.2</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>676602285.2</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>7851739929.5</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>11722783310.6</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>1915432943.8</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>14289544377.6</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>28991897351.5</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>3920350393.1</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>207766207.6</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>5756000.0</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>10095901458.2</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>219553713.2</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>2198096995.0</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>48756295898.2</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>SAS</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>24370850062.4</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>2547120639.9</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1304221181.4</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>268295000.0</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>1075437996.6</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>1729975495.9</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>270096709.9</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1750000000.0</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>571993000.0</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>529046985.1</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>77491628.1</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>48689796.2</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>449771961.1</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>739653515.9</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>140722675.3</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1525209957.7</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>2469629011.8</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>410819385.2</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>151529090.9</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>4424000.0</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>2430576076.0</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>77491628.1</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>625106796.2</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>5761489255.9</td>
        </tr>
        <tr>
            <td>Sri Lanka</td>
            <td>LKA</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1805703222.2</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>37459842.2</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>4891779.5</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>5113457.5</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>5713700.5</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>1375737.7</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>200000.0</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>85925.9</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>15019216.3</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>31746141.7</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>3430115.9</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>20132673.8</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>37459842.2</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>4805853.6</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>200000.0</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>85925.9</td>
        </tr>
        <tr>
            <td>St. Lucia</td>
            <td>LCA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>20332673.8</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>33458473.7</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>6817648.3</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>3070092.3</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>8155461.4</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>1181883.8</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1225216.3</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>567777.8</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>500142.9</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>8000.0</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>21615600.7</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>25303012.3</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>5059986.7</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>24685693.0</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>33458473.7</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>6241870.5</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>1725359.2</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>575777.8</td>
        </tr>
        <tr>
            <td>St. Vincent and the Grenadines</td>
            <td>VCT</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>26411052.2</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>704940261.8</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>93311473.0</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>262918897.8</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>376666146.5</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>40572544.5</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>217194878.8</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>328274115.3</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>52738928.5</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>480113776.6</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>704940261.8</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>93311473.0</td>
        </tr>
        <tr>
            <td>Sudan</td>
            <td>SDN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>480113776.6</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>266925460.4</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>39165280.6</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>159358328.9</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>126505578.0</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>9269996.5</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>147903571.1</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>140419882.4</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>29895284.1</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>307261900.0</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>266925460.4</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>39165280.6</td>
        </tr>
        <tr>
            <td>Syrian Arab Republic</td>
            <td>SYR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>307261900.0</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>89888943.9</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>95265217.6</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>57094000.0</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>73281257.2</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>4600834.4</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>26333637.2</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>59062982.0</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>85288109.5</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>11837580.4</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>132344239.2</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>89888943.9</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>38171217.6</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>467153429.2</td>
        </tr>
        <tr>
            <td>Tajikistan</td>
            <td>TJK</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>334809190.0</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1166055814.5</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>283734011.6</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>104305000.0</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>194944695.3</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>150348676.0</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>40941173.9</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>440124365.3</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>50780712.8</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>141436637.0</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1015707138.5</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>87707124.9</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>336381332.3</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1166055814.5</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>128648298.8</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>45783.8</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>440170149.1</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>50780712.8</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1388218481.4</td>
        </tr>
        <tr>
            <td>Tanzania</td>
            <td>TZA</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>611667000.0</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>301616651.9</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1844227471.1</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>1347170000.0</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>277799616.8</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>301616651.9</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>59731471.1</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>410324000.0</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>498000.0</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>39071571.5</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>26504000.0</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>316871188.3</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>301616651.9</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>86235471.1</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>410822000.0</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>5914706998.3</td>
        </tr>
        <tr>
            <td>Thailand</td>
            <td>THA</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>5597835810.0</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>21799986.4</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>1042000.0</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>9869907.0</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>825000.0</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>11930079.4</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>1042000.0</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>825000.0</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>21799986.4</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>1042000.0</td>
        </tr>
        <tr>
            <td>Timor-Leste</td>
            <td>TLS</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>825000.0</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>236837922.9</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>29685476.6</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>25160550.3</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>79978552.9</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>12931550.3</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>4453240.8</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>310618.7</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>44198800.7</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>156859370.0</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>16443307.6</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>69359351.0</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>236837922.9</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>29374857.9</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>4453240.8</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>310618.7</td>
        </tr>
        <tr>
            <td>Togo</td>
            <td>TGO</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>73812591.8</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>5529604.8</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>2503586.2</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>7554054.0</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>1559371.0</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>24603.4</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2791253.2</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>5529604.8</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>944215.2</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>10345307.2</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>5529604.8</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>2503586.2</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>24603.4</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Tonga</td>
            <td>TON</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>10369910.6</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1820582243.5</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>558379079.9</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>26173000.0</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>507052864.2</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>855186119.9</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>87248174.8</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>735000000.0</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>238989390.1</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>66123380.1</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>17291669.3</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>12030683.8</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>956604000.1</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>947210895.8</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>193716342.4</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1463656864.3</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1802397015.7</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>280964517.2</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>3796971.4</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>893558.5</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>221488.8</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>804920351.5</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>18185227.8</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>251241562.7</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2422062635.8</td>
        </tr>
        <tr>
            <td>Tunisia</td>
            <td>TUN</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>153485420.0</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>2514443147.1</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>12095568642.2</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>7453172920.0</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>646463879.8</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>415269075.4</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>110410777.7</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>6499125000.0</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>3786751212.0</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>1527243953.1</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>509650169.6</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>220044039.8</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2932698678.0</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>1589523902.1</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>524617190.9</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>3579162557.8</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>2004792977.5</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>635027968.6</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>33302064.9</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>572501.8</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>8059671018.0</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>509650169.6</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>4007367753.6</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>51555031005.8</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>TUR</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>39916197430.0</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>6169623.2</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>1514715.9</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>14046164.6</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>2505907.3</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>5831189.2</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>2149000.0</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>19877353.8</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>4654907.3</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>29132060.9</td>
        </tr>
        <tr>
            <td>Turkmenistan</td>
            <td>TKM</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>9254707.1</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1359705707.6</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>221400672.8</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>97451000.0</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>64110341.2</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>538450864.4</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>73813147.0</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>8901204.6</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>14686987.6</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>1351611.1</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>145310077.2</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>806567855.6</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>48784914.7</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>209420418.4</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1345018720.0</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>122598061.7</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>8901204.6</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>14686987.6</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>1351611.1</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>637469740.6</td>
        </tr>
        <tr>
            <td>Uganda</td>
            <td>UGA</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>419148117.6</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>510350370.6</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>3001506404.4</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>1647660000.0</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>95941219.4</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>19809816.8</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>1977107000.0</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>1176828000.0</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>1072472830.3</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>510350370.6</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>153872076.6</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>1168414049.7</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>510350370.6</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>173681893.4</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>158881474.4</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>3336511.0</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>2135988474.4</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>1180164511.0</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>8148995625.6</td>
        </tr>
        <tr>
            <td>Ukraine</td>
            <td>UKR</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>4844593101.5</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1239046975.1</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>436626524.9</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>260318000.0</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>273378640.0</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>503520641.3</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>64937572.1</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>53342975.3</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>7547194.9</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>244240575.6</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>735526333.8</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>103823757.9</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>517619215.6</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1239046975.1</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>168761330.0</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>53342975.3</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>7547194.9</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>2097517190.9</td>
        </tr>
        <tr>
            <td>Uzbekistan</td>
            <td>UZB</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>1526555000.0</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>38626756.0</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>5031805.2</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>10956691.0</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>9007166.6</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>3160158.4</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>2593419.3</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>29619589.4</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>1871646.8</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>13550110.3</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>38626756.0</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>5031805.2</td>
        </tr>
        <tr>
            <td>Vanuatu</td>
            <td>VUT</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>13550110.3</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>521048463.1</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>4159342365.6</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>1111403000.0</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>106054401.7</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>65088096.0</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>13163216.3</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>2551518555.6</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>2810526000.0</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>174069119.8</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>102206207.3</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>8436089.5</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>509512564.6</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>353754159.8</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>206837690.9</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>615566966.3</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>418842255.8</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>220000907.2</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>20017565.5</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>8976368.9</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>2745605240.9</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>102206207.3</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>2827938458.4</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>9878659207.2</td>
        </tr>
        <tr>
            <td>Venezuela, RB</td>
            <td>VEN</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>6517487000.0</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>6494121653.2</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>2120093736.3</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>965351000.0</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>1561158600.3</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>4134438674.8</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>502741840.9</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>13632857.1</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>65622000.0</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>704569299.3</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>25346927.8</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>180617476.7</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>947632152.5</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>2334336050.6</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>405761418.7</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>2508790752.8</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>6468774725.4</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>908503259.6</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>718202156.4</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>25346927.8</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>246239476.7</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>8873505909.2</td>
        </tr>
        <tr>
            <td>Vietnam</td>
            <td>VNM</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>5646513000.0</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>402113863.0</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>77955354.9</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>150087048.6</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>91012892.5</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>25996299.6</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>220743129.9</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>311100970.5</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>51959055.3</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>370830178.5</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>402113863.0</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>77955354.9</td>
        </tr>
        <tr>
            <td>Yemen, Rep.</td>
            <td>YEM</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>370830178.5</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>1502399702.8</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>642613116.2</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>124285000.0</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>211048374.3</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>711130463.7</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>121800491.2</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>DT.AMT.PBND.CD</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, bonds (INT, current US$)</td>
            <td>DT.INT.PBND.CD</td>
            <td>237436000.0</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, commercial banks (AMT, current US$)</td>
            <td>DT.AMT.PCBK.CD</td>
            <td>386100432.2</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, commercial banks (DIS, current US$)</td>
            <td>DT.DIS.PCBK.CD</td>
            <td>383744556.9</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, commercial banks (INT, current US$)</td>
            <td>DT.INT.PCBK.CD</td>
            <td>130206000.0</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>53068964.9</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>392541825.1</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>21418258.1</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>264117339.2</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>1103672288.8</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>143218749.3</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, other private creditors (AMT, current US$)</td>
            <td>DT.AMT.PROP.CD</td>
            <td>34248812.7</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, other private creditors (DIS, current US$)</td>
            <td>DT.DIS.PROP.CD</td>
            <td>14982857.1</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, other private creditors (INT, current US$)</td>
            <td>DT.INT.PROP.CD</td>
            <td>7467366.9</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>DT.AMT.PRVT.CD</td>
            <td>420349244.9</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, private creditors (DIS, current US$)</td>
            <td>DT.DIS.PRVT.CD</td>
            <td>398727414.0</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>PPG, private creditors (INT, current US$)</td>
            <td>DT.INT.PRVT.CD</td>
            <td>375109366.9</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>1217643471.9</td>
        </tr>
        <tr>
            <td>Zambia</td>
            <td>ZMB</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>533176887.8</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>DT.DIS.DLXF.CD</td>
            <td>44396033.7</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>DT.INT.DLXF.CD</td>
            <td>46758660.0</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>DT.INT.DPNG.CD</td>
            <td>30997000.0</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>PPG, bilateral (AMT, current US$)</td>
            <td>DT.AMT.BLAT.CD</td>
            <td>71794214.8</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>DT.DIS.BLAT.CD</td>
            <td>42332836.7</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>PPG, bilateral (INT, current US$)</td>
            <td>DT.INT.BLAT.CD</td>
            <td>11769908.3</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>PPG, multilateral (AMT, current US$)</td>
            <td>DT.AMT.MLAT.CD</td>
            <td>26697905.1</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>PPG, multilateral (DIS, current US$)</td>
            <td>DT.DIS.MLAT.CD</td>
            <td>2063197.0</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>PPG, multilateral (INT, current US$)</td>
            <td>DT.INT.MLAT.CD</td>
            <td>3991751.7</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>DT.AMT.OFFT.CD</td>
            <td>98492119.9</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>DT.DIS.OFFT.CD</td>
            <td>44396033.7</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>PPG, official creditors (INT, current US$)</td>
            <td>DT.INT.OFFT.CD</td>
            <td>15761660.0</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>DT.AMT.DLXF.CD</td>
            <td>461632253.7</td>
        </tr>
        <tr>
            <td>Zimbabwe</td>
            <td>ZWE</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>DT.AMT.DPNG.CD</td>
            <td>363140133.8</td>
        </tr>
    </tbody>
</table>



## 1. Total amount of debt owed by the countries


```sql
%%sql 
SELECT ROUND(SUM(debt)/1000000, 2) AS total_debt 
FROM international_debt; 
```

     * mysql+mysqldb://root:***@localhost/debt
    1 rows affected.
    




<table>
    <thead>
        <tr>
            <th>total_debt</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>3079734.49</td>
        </tr>
    </tbody>
</table>



## 2. Country with the highest debt


```sql
%%sql 
SELECT country_name, SUM(debt) AS total_debt 
FROM international_debt 
GROUP BY country_name 
ORDER BY total_debt DESC 
LIMIT 1;
```

     * mysql+mysqldb://root:***@localhost/debt
    1 rows affected.
    




<table>
    <thead>
        <tr>
            <th>country_name</th>
            <th>total_debt</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>China</td>
            <td>285793494734.2</td>
        </tr>
    </tbody>
</table>



## 3. Average amount of debt across indicators


```sql
%%sql
SELECT 
    indicator_code AS debt_indicator,
    indicator_name,
    round(AVG(debt),2) AS average_debt
FROM international_debt
GROUP BY debt_indicator, indicator_name
ORDER BY average_debt DESC
Limit 10;
```

     * mysql+mysqldb://root:***@localhost/debt
    10 rows affected.
    




<table>
    <thead>
        <tr>
            <th>debt_indicator</th>
            <th>indicator_name</th>
            <th>average_debt</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>DT.AMT.DLXF.CD</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
            <td>5904868401.5</td>
        </tr>
        <tr>
            <td>DT.AMT.DPNG.CD</td>
            <td>Principal repayments on external debt, private nonguaranteed (PNG) (AMT, current US$)</td>
            <td>5161194333.81</td>
        </tr>
        <tr>
            <td>DT.DIS.DLXF.CD</td>
            <td>Disbursements on external debt, long-term (DIS, current US$)</td>
            <td>2152041216.89</td>
        </tr>
        <tr>
            <td>DT.DIS.OFFT.CD</td>
            <td>PPG, official creditors (DIS, current US$)</td>
            <td>1958983452.86</td>
        </tr>
        <tr>
            <td>DT.AMT.PRVT.CD</td>
            <td>PPG, private creditors (AMT, current US$)</td>
            <td>1803694101.96</td>
        </tr>
        <tr>
            <td>DT.INT.DLXF.CD</td>
            <td>Interest payments on external debt, long-term (INT, current US$)</td>
            <td>1644024067.65</td>
        </tr>
        <tr>
            <td>DT.DIS.BLAT.CD</td>
            <td>PPG, bilateral (DIS, current US$)</td>
            <td>1223139290.4</td>
        </tr>
        <tr>
            <td>DT.INT.DPNG.CD</td>
            <td>Interest payments on external debt, private nonguaranteed (PNG) (INT, current US$)</td>
            <td>1220410844.42</td>
        </tr>
        <tr>
            <td>DT.AMT.OFFT.CD</td>
            <td>PPG, official creditors (AMT, current US$)</td>
            <td>1191187963.08</td>
        </tr>
        <tr>
            <td>DT.AMT.PBND.CD</td>
            <td>PPG, bonds (AMT, current US$)</td>
            <td>1082623947.65</td>
        </tr>
    </tbody>
</table>



## 4. The highest amount of principal repayments


```sql
%%sql
SELECT 
    country_name, 
    indicator_name
FROM international_debt
WHERE debt = (SELECT MAX(debt)
            
             FROM international_debt);
```

     * mysql+mysqldb://root:***@localhost/debt
    1 rows affected.
    




<table>
    <thead>
        <tr>
            <th>country_name</th>
            <th>indicator_name</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>China</td>
            <td>Principal repayments on external debt, long-term (AMT, current US$)</td>
        </tr>
    </tbody>
</table>



## 5. The most common debt indicator


```sql
%%sql
SELECT indicator_code , COUNT(*) AS indicator_count
FROM international_debt
GROUP BY indicator_code
ORDER BY indicator_count DESC , indicator_code DESC
Limit 10;
```

     * mysql+mysqldb://root:***@localhost/debt
    10 rows affected.
    




<table>
    <thead>
        <tr>
            <th>indicator_code</th>
            <th>indicator_count</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>DT.INT.OFFT.CD</td>
            <td>124</td>
        </tr>
        <tr>
            <td>DT.INT.MLAT.CD</td>
            <td>124</td>
        </tr>
        <tr>
            <td>DT.INT.DLXF.CD</td>
            <td>124</td>
        </tr>
        <tr>
            <td>DT.AMT.OFFT.CD</td>
            <td>124</td>
        </tr>
        <tr>
            <td>DT.AMT.MLAT.CD</td>
            <td>124</td>
        </tr>
        <tr>
            <td>DT.AMT.DLXF.CD</td>
            <td>124</td>
        </tr>
        <tr>
            <td>DT.DIS.DLXF.CD</td>
            <td>123</td>
        </tr>
        <tr>
            <td>DT.INT.BLAT.CD</td>
            <td>122</td>
        </tr>
        <tr>
            <td>DT.DIS.OFFT.CD</td>
            <td>122</td>
        </tr>
        <tr>
            <td>DT.AMT.BLAT.CD</td>
            <td>122</td>
        </tr>
    </tbody>
</table>



## 6. Maximum debt per country


```sql
%%sql
SELECT country_name, MAX(debt) AS maximum_debt
FROM international_debt
Group by country_name
Order by maximum_debt DESC
Limit 10;
```

     * mysql+mysqldb://root:***@localhost/debt
    10 rows affected.
    




<table>
    <thead>
        <tr>
            <th>country_name</th>
            <th>maximum_debt</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>China</td>
            <td>96218620835.7</td>
        </tr>
        <tr>
            <td>Brazil</td>
            <td>90041840304.1</td>
        </tr>
        <tr>
            <td>Russian Federation</td>
            <td>66589761833.5</td>
        </tr>
        <tr>
            <td>Turkey</td>
            <td>51555031005.8</td>
        </tr>
        <tr>
            <td>South Asia</td>
            <td>48756295898.2</td>
        </tr>
        <tr>
            <td>Least developed countries: UN classification</td>
            <td>40160766261.6</td>
        </tr>
        <tr>
            <td>IDA only</td>
            <td>34531188113.2</td>
        </tr>
        <tr>
            <td>India</td>
            <td>31923507000.8</td>
        </tr>
        <tr>
            <td>Indonesia</td>
            <td>30916112653.8</td>
        </tr>
        <tr>
            <td>Kazakhstan</td>
            <td>27482093686.4</td>
        </tr>
    </tbody>
</table>




```python

```
