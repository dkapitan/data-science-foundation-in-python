
# Exercise 2.8


```python
%matplotlib inline

import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
import numpy as np

pd.options.display.float_format = '{:,.2f}'.format # Print only 2 decimal cases.
```

## (a) Read csv


```python
college = pd.read_csv("../data/College.csv") # Portable import, works on Windows as well.
college
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>Private</th>
      <th>Apps</th>
      <th>Accept</th>
      <th>Enroll</th>
      <th>Top10perc</th>
      <th>Top25perc</th>
      <th>F.Undergrad</th>
      <th>P.Undergrad</th>
      <th>Outstate</th>
      <th>Room.Board</th>
      <th>Books</th>
      <th>Personal</th>
      <th>PhD</th>
      <th>Terminal</th>
      <th>S.F.Ratio</th>
      <th>perc.alumni</th>
      <th>Expend</th>
      <th>Grad.Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Abilene Christian University</td>
      <td>Yes</td>
      <td>1660</td>
      <td>1232</td>
      <td>721</td>
      <td>23</td>
      <td>52</td>
      <td>2885</td>
      <td>537</td>
      <td>7440</td>
      <td>3300</td>
      <td>450</td>
      <td>2200</td>
      <td>70</td>
      <td>78</td>
      <td>18.10</td>
      <td>12</td>
      <td>7041</td>
      <td>60</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Adelphi University</td>
      <td>Yes</td>
      <td>2186</td>
      <td>1924</td>
      <td>512</td>
      <td>16</td>
      <td>29</td>
      <td>2683</td>
      <td>1227</td>
      <td>12280</td>
      <td>6450</td>
      <td>750</td>
      <td>1500</td>
      <td>29</td>
      <td>30</td>
      <td>12.20</td>
      <td>16</td>
      <td>10527</td>
      <td>56</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adrian College</td>
      <td>Yes</td>
      <td>1428</td>
      <td>1097</td>
      <td>336</td>
      <td>22</td>
      <td>50</td>
      <td>1036</td>
      <td>99</td>
      <td>11250</td>
      <td>3750</td>
      <td>400</td>
      <td>1165</td>
      <td>53</td>
      <td>66</td>
      <td>12.90</td>
      <td>30</td>
      <td>8735</td>
      <td>54</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Agnes Scott College</td>
      <td>Yes</td>
      <td>417</td>
      <td>349</td>
      <td>137</td>
      <td>60</td>
      <td>89</td>
      <td>510</td>
      <td>63</td>
      <td>12960</td>
      <td>5450</td>
      <td>450</td>
      <td>875</td>
      <td>92</td>
      <td>97</td>
      <td>7.70</td>
      <td>37</td>
      <td>19016</td>
      <td>59</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Alaska Pacific University</td>
      <td>Yes</td>
      <td>193</td>
      <td>146</td>
      <td>55</td>
      <td>16</td>
      <td>44</td>
      <td>249</td>
      <td>869</td>
      <td>7560</td>
      <td>4120</td>
      <td>800</td>
      <td>1500</td>
      <td>76</td>
      <td>72</td>
      <td>11.90</td>
      <td>2</td>
      <td>10922</td>
      <td>15</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Albertson College</td>
      <td>Yes</td>
      <td>587</td>
      <td>479</td>
      <td>158</td>
      <td>38</td>
      <td>62</td>
      <td>678</td>
      <td>41</td>
      <td>13500</td>
      <td>3335</td>
      <td>500</td>
      <td>675</td>
      <td>67</td>
      <td>73</td>
      <td>9.40</td>
      <td>11</td>
      <td>9727</td>
      <td>55</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Albertus Magnus College</td>
      <td>Yes</td>
      <td>353</td>
      <td>340</td>
      <td>103</td>
      <td>17</td>
      <td>45</td>
      <td>416</td>
      <td>230</td>
      <td>13290</td>
      <td>5720</td>
      <td>500</td>
      <td>1500</td>
      <td>90</td>
      <td>93</td>
      <td>11.50</td>
      <td>26</td>
      <td>8861</td>
      <td>63</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Albion College</td>
      <td>Yes</td>
      <td>1899</td>
      <td>1720</td>
      <td>489</td>
      <td>37</td>
      <td>68</td>
      <td>1594</td>
      <td>32</td>
      <td>13868</td>
      <td>4826</td>
      <td>450</td>
      <td>850</td>
      <td>89</td>
      <td>100</td>
      <td>13.70</td>
      <td>37</td>
      <td>11487</td>
      <td>73</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Albright College</td>
      <td>Yes</td>
      <td>1038</td>
      <td>839</td>
      <td>227</td>
      <td>30</td>
      <td>63</td>
      <td>973</td>
      <td>306</td>
      <td>15595</td>
      <td>4400</td>
      <td>300</td>
      <td>500</td>
      <td>79</td>
      <td>84</td>
      <td>11.30</td>
      <td>23</td>
      <td>11644</td>
      <td>80</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Alderson-Broaddus College</td>
      <td>Yes</td>
      <td>582</td>
      <td>498</td>
      <td>172</td>
      <td>21</td>
      <td>44</td>
      <td>799</td>
      <td>78</td>
      <td>10468</td>
      <td>3380</td>
      <td>660</td>
      <td>1800</td>
      <td>40</td>
      <td>41</td>
      <td>11.50</td>
      <td>15</td>
      <td>8991</td>
      <td>52</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Alfred University</td>
      <td>Yes</td>
      <td>1732</td>
      <td>1425</td>
      <td>472</td>
      <td>37</td>
      <td>75</td>
      <td>1830</td>
      <td>110</td>
      <td>16548</td>
      <td>5406</td>
      <td>500</td>
      <td>600</td>
      <td>82</td>
      <td>88</td>
      <td>11.30</td>
      <td>31</td>
      <td>10932</td>
      <td>73</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Allegheny College</td>
      <td>Yes</td>
      <td>2652</td>
      <td>1900</td>
      <td>484</td>
      <td>44</td>
      <td>77</td>
      <td>1707</td>
      <td>44</td>
      <td>17080</td>
      <td>4440</td>
      <td>400</td>
      <td>600</td>
      <td>73</td>
      <td>91</td>
      <td>9.90</td>
      <td>41</td>
      <td>11711</td>
      <td>76</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Allentown Coll. of St. Francis de Sales</td>
      <td>Yes</td>
      <td>1179</td>
      <td>780</td>
      <td>290</td>
      <td>38</td>
      <td>64</td>
      <td>1130</td>
      <td>638</td>
      <td>9690</td>
      <td>4785</td>
      <td>600</td>
      <td>1000</td>
      <td>60</td>
      <td>84</td>
      <td>13.30</td>
      <td>21</td>
      <td>7940</td>
      <td>74</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Alma College</td>
      <td>Yes</td>
      <td>1267</td>
      <td>1080</td>
      <td>385</td>
      <td>44</td>
      <td>73</td>
      <td>1306</td>
      <td>28</td>
      <td>12572</td>
      <td>4552</td>
      <td>400</td>
      <td>400</td>
      <td>79</td>
      <td>87</td>
      <td>15.30</td>
      <td>32</td>
      <td>9305</td>
      <td>68</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Alverno College</td>
      <td>Yes</td>
      <td>494</td>
      <td>313</td>
      <td>157</td>
      <td>23</td>
      <td>46</td>
      <td>1317</td>
      <td>1235</td>
      <td>8352</td>
      <td>3640</td>
      <td>650</td>
      <td>2449</td>
      <td>36</td>
      <td>69</td>
      <td>11.10</td>
      <td>26</td>
      <td>8127</td>
      <td>55</td>
    </tr>
    <tr>
      <th>15</th>
      <td>American International College</td>
      <td>Yes</td>
      <td>1420</td>
      <td>1093</td>
      <td>220</td>
      <td>9</td>
      <td>22</td>
      <td>1018</td>
      <td>287</td>
      <td>8700</td>
      <td>4780</td>
      <td>450</td>
      <td>1400</td>
      <td>78</td>
      <td>84</td>
      <td>14.70</td>
      <td>19</td>
      <td>7355</td>
      <td>69</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Amherst College</td>
      <td>Yes</td>
      <td>4302</td>
      <td>992</td>
      <td>418</td>
      <td>83</td>
      <td>96</td>
      <td>1593</td>
      <td>5</td>
      <td>19760</td>
      <td>5300</td>
      <td>660</td>
      <td>1598</td>
      <td>93</td>
      <td>98</td>
      <td>8.40</td>
      <td>63</td>
      <td>21424</td>
      <td>100</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Anderson University</td>
      <td>Yes</td>
      <td>1216</td>
      <td>908</td>
      <td>423</td>
      <td>19</td>
      <td>40</td>
      <td>1819</td>
      <td>281</td>
      <td>10100</td>
      <td>3520</td>
      <td>550</td>
      <td>1100</td>
      <td>48</td>
      <td>61</td>
      <td>12.10</td>
      <td>14</td>
      <td>7994</td>
      <td>59</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Andrews University</td>
      <td>Yes</td>
      <td>1130</td>
      <td>704</td>
      <td>322</td>
      <td>14</td>
      <td>23</td>
      <td>1586</td>
      <td>326</td>
      <td>9996</td>
      <td>3090</td>
      <td>900</td>
      <td>1320</td>
      <td>62</td>
      <td>66</td>
      <td>11.50</td>
      <td>18</td>
      <td>10908</td>
      <td>46</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Angelo State University</td>
      <td>No</td>
      <td>3540</td>
      <td>2001</td>
      <td>1016</td>
      <td>24</td>
      <td>54</td>
      <td>4190</td>
      <td>1512</td>
      <td>5130</td>
      <td>3592</td>
      <td>500</td>
      <td>2000</td>
      <td>60</td>
      <td>62</td>
      <td>23.10</td>
      <td>5</td>
      <td>4010</td>
      <td>34</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Antioch University</td>
      <td>Yes</td>
      <td>713</td>
      <td>661</td>
      <td>252</td>
      <td>25</td>
      <td>44</td>
      <td>712</td>
      <td>23</td>
      <td>15476</td>
      <td>3336</td>
      <td>400</td>
      <td>1100</td>
      <td>69</td>
      <td>82</td>
      <td>11.30</td>
      <td>35</td>
      <td>42926</td>
      <td>48</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Appalachian State University</td>
      <td>No</td>
      <td>7313</td>
      <td>4664</td>
      <td>1910</td>
      <td>20</td>
      <td>63</td>
      <td>9940</td>
      <td>1035</td>
      <td>6806</td>
      <td>2540</td>
      <td>96</td>
      <td>2000</td>
      <td>83</td>
      <td>96</td>
      <td>18.30</td>
      <td>14</td>
      <td>5854</td>
      <td>70</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Aquinas College</td>
      <td>Yes</td>
      <td>619</td>
      <td>516</td>
      <td>219</td>
      <td>20</td>
      <td>51</td>
      <td>1251</td>
      <td>767</td>
      <td>11208</td>
      <td>4124</td>
      <td>350</td>
      <td>1615</td>
      <td>55</td>
      <td>65</td>
      <td>12.70</td>
      <td>25</td>
      <td>6584</td>
      <td>65</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Arizona State University Main campus</td>
      <td>No</td>
      <td>12809</td>
      <td>10308</td>
      <td>3761</td>
      <td>24</td>
      <td>49</td>
      <td>22593</td>
      <td>7585</td>
      <td>7434</td>
      <td>4850</td>
      <td>700</td>
      <td>2100</td>
      <td>88</td>
      <td>93</td>
      <td>18.90</td>
      <td>5</td>
      <td>4602</td>
      <td>48</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Arkansas College (Lyon College)</td>
      <td>Yes</td>
      <td>708</td>
      <td>334</td>
      <td>166</td>
      <td>46</td>
      <td>74</td>
      <td>530</td>
      <td>182</td>
      <td>8644</td>
      <td>3922</td>
      <td>500</td>
      <td>800</td>
      <td>79</td>
      <td>88</td>
      <td>12.60</td>
      <td>24</td>
      <td>14579</td>
      <td>54</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Arkansas Tech University</td>
      <td>No</td>
      <td>1734</td>
      <td>1729</td>
      <td>951</td>
      <td>12</td>
      <td>52</td>
      <td>3602</td>
      <td>939</td>
      <td>3460</td>
      <td>2650</td>
      <td>450</td>
      <td>1000</td>
      <td>57</td>
      <td>60</td>
      <td>19.60</td>
      <td>5</td>
      <td>4739</td>
      <td>48</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Assumption College</td>
      <td>Yes</td>
      <td>2135</td>
      <td>1700</td>
      <td>491</td>
      <td>23</td>
      <td>59</td>
      <td>1708</td>
      <td>689</td>
      <td>12000</td>
      <td>5920</td>
      <td>500</td>
      <td>500</td>
      <td>93</td>
      <td>93</td>
      <td>13.80</td>
      <td>30</td>
      <td>7100</td>
      <td>88</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Auburn University-Main Campus</td>
      <td>No</td>
      <td>7548</td>
      <td>6791</td>
      <td>3070</td>
      <td>25</td>
      <td>57</td>
      <td>16262</td>
      <td>1716</td>
      <td>6300</td>
      <td>3933</td>
      <td>600</td>
      <td>1908</td>
      <td>85</td>
      <td>91</td>
      <td>16.70</td>
      <td>18</td>
      <td>6642</td>
      <td>69</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Augsburg College</td>
      <td>Yes</td>
      <td>662</td>
      <td>513</td>
      <td>257</td>
      <td>12</td>
      <td>30</td>
      <td>2074</td>
      <td>726</td>
      <td>11902</td>
      <td>4372</td>
      <td>540</td>
      <td>950</td>
      <td>65</td>
      <td>65</td>
      <td>12.80</td>
      <td>31</td>
      <td>7836</td>
      <td>58</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Augustana College IL</td>
      <td>Yes</td>
      <td>1879</td>
      <td>1658</td>
      <td>497</td>
      <td>36</td>
      <td>69</td>
      <td>1950</td>
      <td>38</td>
      <td>13353</td>
      <td>4173</td>
      <td>540</td>
      <td>821</td>
      <td>78</td>
      <td>83</td>
      <td>12.70</td>
      <td>40</td>
      <td>9220</td>
      <td>71</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>747</th>
      <td>Westfield State College</td>
      <td>No</td>
      <td>3100</td>
      <td>2150</td>
      <td>825</td>
      <td>3</td>
      <td>20</td>
      <td>3234</td>
      <td>941</td>
      <td>5542</td>
      <td>3788</td>
      <td>500</td>
      <td>1300</td>
      <td>75</td>
      <td>79</td>
      <td>15.70</td>
      <td>20</td>
      <td>4222</td>
      <td>65</td>
    </tr>
    <tr>
      <th>748</th>
      <td>Westminster College MO</td>
      <td>Yes</td>
      <td>662</td>
      <td>553</td>
      <td>184</td>
      <td>20</td>
      <td>43</td>
      <td>665</td>
      <td>37</td>
      <td>10720</td>
      <td>4050</td>
      <td>600</td>
      <td>1650</td>
      <td>66</td>
      <td>70</td>
      <td>12.50</td>
      <td>20</td>
      <td>7925</td>
      <td>62</td>
    </tr>
    <tr>
      <th>749</th>
      <td>Westminster College</td>
      <td>Yes</td>
      <td>996</td>
      <td>866</td>
      <td>377</td>
      <td>29</td>
      <td>58</td>
      <td>1411</td>
      <td>72</td>
      <td>12065</td>
      <td>3615</td>
      <td>430</td>
      <td>685</td>
      <td>62</td>
      <td>78</td>
      <td>12.50</td>
      <td>41</td>
      <td>8596</td>
      <td>80</td>
    </tr>
    <tr>
      <th>750</th>
      <td>Westminster College of Salt Lake City</td>
      <td>Yes</td>
      <td>917</td>
      <td>720</td>
      <td>213</td>
      <td>21</td>
      <td>60</td>
      <td>979</td>
      <td>743</td>
      <td>8820</td>
      <td>4050</td>
      <td>600</td>
      <td>2025</td>
      <td>68</td>
      <td>83</td>
      <td>10.50</td>
      <td>34</td>
      <td>7170</td>
      <td>50</td>
    </tr>
    <tr>
      <th>751</th>
      <td>Westmont College</td>
      <td>No</td>
      <td>950</td>
      <td>713</td>
      <td>351</td>
      <td>42</td>
      <td>72</td>
      <td>1276</td>
      <td>9</td>
      <td>14320</td>
      <td>5304</td>
      <td>490</td>
      <td>1410</td>
      <td>77</td>
      <td>77</td>
      <td>14.90</td>
      <td>17</td>
      <td>8837</td>
      <td>87</td>
    </tr>
    <tr>
      <th>752</th>
      <td>Wheaton College IL</td>
      <td>Yes</td>
      <td>1432</td>
      <td>920</td>
      <td>548</td>
      <td>56</td>
      <td>84</td>
      <td>2200</td>
      <td>56</td>
      <td>11480</td>
      <td>4200</td>
      <td>530</td>
      <td>1400</td>
      <td>81</td>
      <td>83</td>
      <td>12.70</td>
      <td>40</td>
      <td>11916</td>
      <td>85</td>
    </tr>
    <tr>
      <th>753</th>
      <td>Westminster College PA</td>
      <td>Yes</td>
      <td>1738</td>
      <td>1373</td>
      <td>417</td>
      <td>21</td>
      <td>55</td>
      <td>1335</td>
      <td>30</td>
      <td>18460</td>
      <td>5970</td>
      <td>700</td>
      <td>850</td>
      <td>92</td>
      <td>96</td>
      <td>13.20</td>
      <td>41</td>
      <td>22704</td>
      <td>71</td>
    </tr>
    <tr>
      <th>754</th>
      <td>Wheeling Jesuit College</td>
      <td>Yes</td>
      <td>903</td>
      <td>755</td>
      <td>213</td>
      <td>15</td>
      <td>49</td>
      <td>971</td>
      <td>305</td>
      <td>10500</td>
      <td>4545</td>
      <td>600</td>
      <td>600</td>
      <td>66</td>
      <td>71</td>
      <td>14.10</td>
      <td>27</td>
      <td>7494</td>
      <td>72</td>
    </tr>
    <tr>
      <th>755</th>
      <td>Whitman College</td>
      <td>Yes</td>
      <td>1861</td>
      <td>998</td>
      <td>359</td>
      <td>45</td>
      <td>77</td>
      <td>1220</td>
      <td>46</td>
      <td>16670</td>
      <td>4900</td>
      <td>750</td>
      <td>800</td>
      <td>80</td>
      <td>83</td>
      <td>10.50</td>
      <td>51</td>
      <td>13198</td>
      <td>72</td>
    </tr>
    <tr>
      <th>756</th>
      <td>Whittier College</td>
      <td>Yes</td>
      <td>1681</td>
      <td>1069</td>
      <td>344</td>
      <td>35</td>
      <td>63</td>
      <td>1235</td>
      <td>30</td>
      <td>16249</td>
      <td>5699</td>
      <td>500</td>
      <td>1998</td>
      <td>84</td>
      <td>92</td>
      <td>13.60</td>
      <td>29</td>
      <td>11778</td>
      <td>52</td>
    </tr>
    <tr>
      <th>757</th>
      <td>Whitworth College</td>
      <td>Yes</td>
      <td>1121</td>
      <td>926</td>
      <td>372</td>
      <td>43</td>
      <td>70</td>
      <td>1270</td>
      <td>160</td>
      <td>12660</td>
      <td>4500</td>
      <td>678</td>
      <td>2424</td>
      <td>80</td>
      <td>80</td>
      <td>16.90</td>
      <td>20</td>
      <td>8328</td>
      <td>80</td>
    </tr>
    <tr>
      <th>758</th>
      <td>Widener University</td>
      <td>Yes</td>
      <td>2139</td>
      <td>1492</td>
      <td>502</td>
      <td>24</td>
      <td>64</td>
      <td>2186</td>
      <td>2171</td>
      <td>12350</td>
      <td>5370</td>
      <td>500</td>
      <td>1350</td>
      <td>88</td>
      <td>86</td>
      <td>12.60</td>
      <td>19</td>
      <td>9603</td>
      <td>63</td>
    </tr>
    <tr>
      <th>759</th>
      <td>Wilkes University</td>
      <td>Yes</td>
      <td>1631</td>
      <td>1431</td>
      <td>434</td>
      <td>15</td>
      <td>36</td>
      <td>1803</td>
      <td>603</td>
      <td>11150</td>
      <td>5130</td>
      <td>550</td>
      <td>1260</td>
      <td>78</td>
      <td>92</td>
      <td>13.30</td>
      <td>24</td>
      <td>8543</td>
      <td>67</td>
    </tr>
    <tr>
      <th>760</th>
      <td>Willamette University</td>
      <td>Yes</td>
      <td>1658</td>
      <td>1327</td>
      <td>395</td>
      <td>49</td>
      <td>80</td>
      <td>1595</td>
      <td>159</td>
      <td>14800</td>
      <td>4620</td>
      <td>400</td>
      <td>790</td>
      <td>91</td>
      <td>94</td>
      <td>13.30</td>
      <td>37</td>
      <td>10779</td>
      <td>68</td>
    </tr>
    <tr>
      <th>761</th>
      <td>William Jewell College</td>
      <td>Yes</td>
      <td>663</td>
      <td>547</td>
      <td>315</td>
      <td>32</td>
      <td>67</td>
      <td>1279</td>
      <td>75</td>
      <td>10060</td>
      <td>2970</td>
      <td>500</td>
      <td>2600</td>
      <td>74</td>
      <td>80</td>
      <td>11.20</td>
      <td>19</td>
      <td>7885</td>
      <td>59</td>
    </tr>
    <tr>
      <th>762</th>
      <td>William Woods University</td>
      <td>Yes</td>
      <td>469</td>
      <td>435</td>
      <td>227</td>
      <td>17</td>
      <td>39</td>
      <td>851</td>
      <td>120</td>
      <td>10535</td>
      <td>4365</td>
      <td>550</td>
      <td>3700</td>
      <td>39</td>
      <td>66</td>
      <td>12.90</td>
      <td>16</td>
      <td>7438</td>
      <td>52</td>
    </tr>
    <tr>
      <th>763</th>
      <td>Williams College</td>
      <td>Yes</td>
      <td>4186</td>
      <td>1245</td>
      <td>526</td>
      <td>81</td>
      <td>96</td>
      <td>1988</td>
      <td>29</td>
      <td>19629</td>
      <td>5790</td>
      <td>500</td>
      <td>1200</td>
      <td>94</td>
      <td>99</td>
      <td>9.00</td>
      <td>64</td>
      <td>22014</td>
      <td>99</td>
    </tr>
    <tr>
      <th>764</th>
      <td>Wilson College</td>
      <td>Yes</td>
      <td>167</td>
      <td>130</td>
      <td>46</td>
      <td>16</td>
      <td>50</td>
      <td>199</td>
      <td>676</td>
      <td>11428</td>
      <td>5084</td>
      <td>450</td>
      <td>475</td>
      <td>67</td>
      <td>76</td>
      <td>8.30</td>
      <td>43</td>
      <td>10291</td>
      <td>67</td>
    </tr>
    <tr>
      <th>765</th>
      <td>Wingate College</td>
      <td>Yes</td>
      <td>1239</td>
      <td>1017</td>
      <td>383</td>
      <td>10</td>
      <td>34</td>
      <td>1207</td>
      <td>157</td>
      <td>7820</td>
      <td>3400</td>
      <td>550</td>
      <td>1550</td>
      <td>69</td>
      <td>81</td>
      <td>13.90</td>
      <td>8</td>
      <td>7264</td>
      <td>91</td>
    </tr>
    <tr>
      <th>766</th>
      <td>Winona State University</td>
      <td>No</td>
      <td>3325</td>
      <td>2047</td>
      <td>1301</td>
      <td>20</td>
      <td>45</td>
      <td>5800</td>
      <td>872</td>
      <td>4200</td>
      <td>2700</td>
      <td>300</td>
      <td>1200</td>
      <td>53</td>
      <td>60</td>
      <td>20.20</td>
      <td>18</td>
      <td>5318</td>
      <td>58</td>
    </tr>
    <tr>
      <th>767</th>
      <td>Winthrop University</td>
      <td>No</td>
      <td>2320</td>
      <td>1805</td>
      <td>769</td>
      <td>24</td>
      <td>61</td>
      <td>3395</td>
      <td>670</td>
      <td>6400</td>
      <td>3392</td>
      <td>580</td>
      <td>2150</td>
      <td>71</td>
      <td>80</td>
      <td>12.80</td>
      <td>26</td>
      <td>6729</td>
      <td>59</td>
    </tr>
    <tr>
      <th>768</th>
      <td>Wisconsin Lutheran College</td>
      <td>Yes</td>
      <td>152</td>
      <td>128</td>
      <td>75</td>
      <td>17</td>
      <td>41</td>
      <td>282</td>
      <td>22</td>
      <td>9100</td>
      <td>3700</td>
      <td>500</td>
      <td>1400</td>
      <td>48</td>
      <td>48</td>
      <td>8.50</td>
      <td>26</td>
      <td>8960</td>
      <td>50</td>
    </tr>
    <tr>
      <th>769</th>
      <td>Wittenberg University</td>
      <td>Yes</td>
      <td>1979</td>
      <td>1739</td>
      <td>575</td>
      <td>42</td>
      <td>68</td>
      <td>1980</td>
      <td>144</td>
      <td>15948</td>
      <td>4404</td>
      <td>400</td>
      <td>800</td>
      <td>82</td>
      <td>95</td>
      <td>12.80</td>
      <td>29</td>
      <td>10414</td>
      <td>78</td>
    </tr>
    <tr>
      <th>770</th>
      <td>Wofford College</td>
      <td>Yes</td>
      <td>1501</td>
      <td>935</td>
      <td>273</td>
      <td>51</td>
      <td>83</td>
      <td>1059</td>
      <td>34</td>
      <td>12680</td>
      <td>4150</td>
      <td>605</td>
      <td>1440</td>
      <td>91</td>
      <td>92</td>
      <td>15.30</td>
      <td>42</td>
      <td>7875</td>
      <td>75</td>
    </tr>
    <tr>
      <th>771</th>
      <td>Worcester Polytechnic Institute</td>
      <td>Yes</td>
      <td>2768</td>
      <td>2314</td>
      <td>682</td>
      <td>49</td>
      <td>86</td>
      <td>2802</td>
      <td>86</td>
      <td>15884</td>
      <td>5370</td>
      <td>530</td>
      <td>730</td>
      <td>92</td>
      <td>94</td>
      <td>15.20</td>
      <td>34</td>
      <td>10774</td>
      <td>82</td>
    </tr>
    <tr>
      <th>772</th>
      <td>Worcester State College</td>
      <td>No</td>
      <td>2197</td>
      <td>1515</td>
      <td>543</td>
      <td>4</td>
      <td>26</td>
      <td>3089</td>
      <td>2029</td>
      <td>6797</td>
      <td>3900</td>
      <td>500</td>
      <td>1200</td>
      <td>60</td>
      <td>60</td>
      <td>21.00</td>
      <td>14</td>
      <td>4469</td>
      <td>40</td>
    </tr>
    <tr>
      <th>773</th>
      <td>Xavier University</td>
      <td>Yes</td>
      <td>1959</td>
      <td>1805</td>
      <td>695</td>
      <td>24</td>
      <td>47</td>
      <td>2849</td>
      <td>1107</td>
      <td>11520</td>
      <td>4960</td>
      <td>600</td>
      <td>1250</td>
      <td>73</td>
      <td>75</td>
      <td>13.30</td>
      <td>31</td>
      <td>9189</td>
      <td>83</td>
    </tr>
    <tr>
      <th>774</th>
      <td>Xavier University of Louisiana</td>
      <td>Yes</td>
      <td>2097</td>
      <td>1915</td>
      <td>695</td>
      <td>34</td>
      <td>61</td>
      <td>2793</td>
      <td>166</td>
      <td>6900</td>
      <td>4200</td>
      <td>617</td>
      <td>781</td>
      <td>67</td>
      <td>75</td>
      <td>14.40</td>
      <td>20</td>
      <td>8323</td>
      <td>49</td>
    </tr>
    <tr>
      <th>775</th>
      <td>Yale University</td>
      <td>Yes</td>
      <td>10705</td>
      <td>2453</td>
      <td>1317</td>
      <td>95</td>
      <td>99</td>
      <td>5217</td>
      <td>83</td>
      <td>19840</td>
      <td>6510</td>
      <td>630</td>
      <td>2115</td>
      <td>96</td>
      <td>96</td>
      <td>5.80</td>
      <td>49</td>
      <td>40386</td>
      <td>99</td>
    </tr>
    <tr>
      <th>776</th>
      <td>York College of Pennsylvania</td>
      <td>Yes</td>
      <td>2989</td>
      <td>1855</td>
      <td>691</td>
      <td>28</td>
      <td>63</td>
      <td>2988</td>
      <td>1726</td>
      <td>4990</td>
      <td>3560</td>
      <td>500</td>
      <td>1250</td>
      <td>75</td>
      <td>75</td>
      <td>18.10</td>
      <td>28</td>
      <td>4509</td>
      <td>99</td>
    </tr>
  </tbody>
</table>
<p>777 rows × 19 columns</p>
</div>



## (b) University names as index

The fix() function in R (similar to edit()) allows on-the-fly edit to the dataframe by invoking an editor.
Further details can be found [here](https://stat.ethz.ch/R-manual/R-devel/library/utils/html/edit.html) and [here](http://stackoverflow.com/questions/34265643/difference-betweeen-fix-and-edit-in-r).


```python
# [1]
college = college.set_index("Unnamed: 0") # The default option 'drop=True', deletes the column
college.index.name = 'Names'
college.head()
# The empty row below the columns names (e.g. Private, Apps, etc.) is there because the index has a name and that creates an additional row.
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Private</th>
      <th>Apps</th>
      <th>Accept</th>
      <th>Enroll</th>
      <th>Top10perc</th>
      <th>Top25perc</th>
      <th>F.Undergrad</th>
      <th>P.Undergrad</th>
      <th>Outstate</th>
      <th>Room.Board</th>
      <th>Books</th>
      <th>Personal</th>
      <th>PhD</th>
      <th>Terminal</th>
      <th>S.F.Ratio</th>
      <th>perc.alumni</th>
      <th>Expend</th>
      <th>Grad.Rate</th>
    </tr>
    <tr>
      <th>Names</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Abilene Christian University</th>
      <td>Yes</td>
      <td>1660</td>
      <td>1232</td>
      <td>721</td>
      <td>23</td>
      <td>52</td>
      <td>2885</td>
      <td>537</td>
      <td>7440</td>
      <td>3300</td>
      <td>450</td>
      <td>2200</td>
      <td>70</td>
      <td>78</td>
      <td>18.10</td>
      <td>12</td>
      <td>7041</td>
      <td>60</td>
    </tr>
    <tr>
      <th>Adelphi University</th>
      <td>Yes</td>
      <td>2186</td>
      <td>1924</td>
      <td>512</td>
      <td>16</td>
      <td>29</td>
      <td>2683</td>
      <td>1227</td>
      <td>12280</td>
      <td>6450</td>
      <td>750</td>
      <td>1500</td>
      <td>29</td>
      <td>30</td>
      <td>12.20</td>
      <td>16</td>
      <td>10527</td>
      <td>56</td>
    </tr>
    <tr>
      <th>Adrian College</th>
      <td>Yes</td>
      <td>1428</td>
      <td>1097</td>
      <td>336</td>
      <td>22</td>
      <td>50</td>
      <td>1036</td>
      <td>99</td>
      <td>11250</td>
      <td>3750</td>
      <td>400</td>
      <td>1165</td>
      <td>53</td>
      <td>66</td>
      <td>12.90</td>
      <td>30</td>
      <td>8735</td>
      <td>54</td>
    </tr>
    <tr>
      <th>Agnes Scott College</th>
      <td>Yes</td>
      <td>417</td>
      <td>349</td>
      <td>137</td>
      <td>60</td>
      <td>89</td>
      <td>510</td>
      <td>63</td>
      <td>12960</td>
      <td>5450</td>
      <td>450</td>
      <td>875</td>
      <td>92</td>
      <td>97</td>
      <td>7.70</td>
      <td>37</td>
      <td>19016</td>
      <td>59</td>
    </tr>
    <tr>
      <th>Alaska Pacific University</th>
      <td>Yes</td>
      <td>193</td>
      <td>146</td>
      <td>55</td>
      <td>16</td>
      <td>44</td>
      <td>249</td>
      <td>869</td>
      <td>7560</td>
      <td>4120</td>
      <td>800</td>
      <td>1500</td>
      <td>76</td>
      <td>72</td>
      <td>11.90</td>
      <td>2</td>
      <td>10922</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>



[1] [https://campus.datacamp.com/courses/manipulating-dataframes-with-pandas/advanced-indexing?ex=1](https://campus.datacamp.com/courses/manipulating-dataframes-with-pandas/advanced-indexing?ex=1) 


```python
# Alternative solution: We could have done this all in one less line with:
college = pd.read_csv('../data/College.csv', index_col='Unnamed: 0')
college.index.name = 'Names'
college.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Private</th>
      <th>Apps</th>
      <th>Accept</th>
      <th>Enroll</th>
      <th>Top10perc</th>
      <th>Top25perc</th>
      <th>F.Undergrad</th>
      <th>P.Undergrad</th>
      <th>Outstate</th>
      <th>Room.Board</th>
      <th>Books</th>
      <th>Personal</th>
      <th>PhD</th>
      <th>Terminal</th>
      <th>S.F.Ratio</th>
      <th>perc.alumni</th>
      <th>Expend</th>
      <th>Grad.Rate</th>
    </tr>
    <tr>
      <th>Names</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Abilene Christian University</th>
      <td>Yes</td>
      <td>1660</td>
      <td>1232</td>
      <td>721</td>
      <td>23</td>
      <td>52</td>
      <td>2885</td>
      <td>537</td>
      <td>7440</td>
      <td>3300</td>
      <td>450</td>
      <td>2200</td>
      <td>70</td>
      <td>78</td>
      <td>18.10</td>
      <td>12</td>
      <td>7041</td>
      <td>60</td>
    </tr>
    <tr>
      <th>Adelphi University</th>
      <td>Yes</td>
      <td>2186</td>
      <td>1924</td>
      <td>512</td>
      <td>16</td>
      <td>29</td>
      <td>2683</td>
      <td>1227</td>
      <td>12280</td>
      <td>6450</td>
      <td>750</td>
      <td>1500</td>
      <td>29</td>
      <td>30</td>
      <td>12.20</td>
      <td>16</td>
      <td>10527</td>
      <td>56</td>
    </tr>
    <tr>
      <th>Adrian College</th>
      <td>Yes</td>
      <td>1428</td>
      <td>1097</td>
      <td>336</td>
      <td>22</td>
      <td>50</td>
      <td>1036</td>
      <td>99</td>
      <td>11250</td>
      <td>3750</td>
      <td>400</td>
      <td>1165</td>
      <td>53</td>
      <td>66</td>
      <td>12.90</td>
      <td>30</td>
      <td>8735</td>
      <td>54</td>
    </tr>
    <tr>
      <th>Agnes Scott College</th>
      <td>Yes</td>
      <td>417</td>
      <td>349</td>
      <td>137</td>
      <td>60</td>
      <td>89</td>
      <td>510</td>
      <td>63</td>
      <td>12960</td>
      <td>5450</td>
      <td>450</td>
      <td>875</td>
      <td>92</td>
      <td>97</td>
      <td>7.70</td>
      <td>37</td>
      <td>19016</td>
      <td>59</td>
    </tr>
    <tr>
      <th>Alaska Pacific University</th>
      <td>Yes</td>
      <td>193</td>
      <td>146</td>
      <td>55</td>
      <td>16</td>
      <td>44</td>
      <td>249</td>
      <td>869</td>
      <td>7560</td>
      <td>4120</td>
      <td>800</td>
      <td>1500</td>
      <td>76</td>
      <td>72</td>
      <td>11.90</td>
      <td>2</td>
      <td>10922</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>



## (c) 
### i. Summary


```python
college.describe(include='all')
# [2, 3, 4] Without the 'all' option, the column 'Private' is not shown because it is categorical
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Private</th>
      <th>Apps</th>
      <th>Accept</th>
      <th>Enroll</th>
      <th>Top10perc</th>
      <th>Top25perc</th>
      <th>F.Undergrad</th>
      <th>P.Undergrad</th>
      <th>Outstate</th>
      <th>Room.Board</th>
      <th>Books</th>
      <th>Personal</th>
      <th>PhD</th>
      <th>Terminal</th>
      <th>S.F.Ratio</th>
      <th>perc.alumni</th>
      <th>Expend</th>
      <th>Grad.Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>777</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>2</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
    </tr>
    <tr>
      <th>top</th>
      <td>Yes</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>565</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
      <td>nan</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>NaN</td>
      <td>3,001.64</td>
      <td>2,018.80</td>
      <td>779.97</td>
      <td>27.56</td>
      <td>55.80</td>
      <td>3,699.91</td>
      <td>855.30</td>
      <td>10,440.67</td>
      <td>4,357.53</td>
      <td>549.38</td>
      <td>1,340.64</td>
      <td>72.66</td>
      <td>79.70</td>
      <td>14.09</td>
      <td>22.74</td>
      <td>9,660.17</td>
      <td>65.46</td>
    </tr>
    <tr>
      <th>std</th>
      <td>NaN</td>
      <td>3,870.20</td>
      <td>2,451.11</td>
      <td>929.18</td>
      <td>17.64</td>
      <td>19.80</td>
      <td>4,850.42</td>
      <td>1,522.43</td>
      <td>4,023.02</td>
      <td>1,096.70</td>
      <td>165.11</td>
      <td>677.07</td>
      <td>16.33</td>
      <td>14.72</td>
      <td>3.96</td>
      <td>12.39</td>
      <td>5,221.77</td>
      <td>17.18</td>
    </tr>
    <tr>
      <th>min</th>
      <td>NaN</td>
      <td>81.00</td>
      <td>72.00</td>
      <td>35.00</td>
      <td>1.00</td>
      <td>9.00</td>
      <td>139.00</td>
      <td>1.00</td>
      <td>2,340.00</td>
      <td>1,780.00</td>
      <td>96.00</td>
      <td>250.00</td>
      <td>8.00</td>
      <td>24.00</td>
      <td>2.50</td>
      <td>0.00</td>
      <td>3,186.00</td>
      <td>10.00</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>NaN</td>
      <td>776.00</td>
      <td>604.00</td>
      <td>242.00</td>
      <td>15.00</td>
      <td>41.00</td>
      <td>992.00</td>
      <td>95.00</td>
      <td>7,320.00</td>
      <td>3,597.00</td>
      <td>470.00</td>
      <td>850.00</td>
      <td>62.00</td>
      <td>71.00</td>
      <td>11.50</td>
      <td>13.00</td>
      <td>6,751.00</td>
      <td>53.00</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>NaN</td>
      <td>1,558.00</td>
      <td>1,110.00</td>
      <td>434.00</td>
      <td>23.00</td>
      <td>54.00</td>
      <td>1,707.00</td>
      <td>353.00</td>
      <td>9,990.00</td>
      <td>4,200.00</td>
      <td>500.00</td>
      <td>1,200.00</td>
      <td>75.00</td>
      <td>82.00</td>
      <td>13.60</td>
      <td>21.00</td>
      <td>8,377.00</td>
      <td>65.00</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>NaN</td>
      <td>3,624.00</td>
      <td>2,424.00</td>
      <td>902.00</td>
      <td>35.00</td>
      <td>69.00</td>
      <td>4,005.00</td>
      <td>967.00</td>
      <td>12,925.00</td>
      <td>5,050.00</td>
      <td>600.00</td>
      <td>1,700.00</td>
      <td>85.00</td>
      <td>92.00</td>
      <td>16.50</td>
      <td>31.00</td>
      <td>10,830.00</td>
      <td>78.00</td>
    </tr>
    <tr>
      <th>max</th>
      <td>NaN</td>
      <td>48,094.00</td>
      <td>26,330.00</td>
      <td>6,392.00</td>
      <td>96.00</td>
      <td>100.00</td>
      <td>31,643.00</td>
      <td>21,836.00</td>
      <td>21,700.00</td>
      <td>8,124.00</td>
      <td>2,340.00</td>
      <td>6,800.00</td>
      <td>103.00</td>
      <td>100.00</td>
      <td>39.80</td>
      <td>64.00</td>
      <td>56,233.00</td>
      <td>118.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Alternative solution: call describe twice. One on number, and another on object.
college.describe(include=['number'])
# or college.describe(include=[np.number])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Apps</th>
      <th>Accept</th>
      <th>Enroll</th>
      <th>Top10perc</th>
      <th>Top25perc</th>
      <th>F.Undergrad</th>
      <th>P.Undergrad</th>
      <th>Outstate</th>
      <th>Room.Board</th>
      <th>Books</th>
      <th>Personal</th>
      <th>PhD</th>
      <th>Terminal</th>
      <th>S.F.Ratio</th>
      <th>perc.alumni</th>
      <th>Expend</th>
      <th>Grad.Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
      <td>777.00</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>3,001.64</td>
      <td>2,018.80</td>
      <td>779.97</td>
      <td>27.56</td>
      <td>55.80</td>
      <td>3,699.91</td>
      <td>855.30</td>
      <td>10,440.67</td>
      <td>4,357.53</td>
      <td>549.38</td>
      <td>1,340.64</td>
      <td>72.66</td>
      <td>79.70</td>
      <td>14.09</td>
      <td>22.74</td>
      <td>9,660.17</td>
      <td>65.46</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3,870.20</td>
      <td>2,451.11</td>
      <td>929.18</td>
      <td>17.64</td>
      <td>19.80</td>
      <td>4,850.42</td>
      <td>1,522.43</td>
      <td>4,023.02</td>
      <td>1,096.70</td>
      <td>165.11</td>
      <td>677.07</td>
      <td>16.33</td>
      <td>14.72</td>
      <td>3.96</td>
      <td>12.39</td>
      <td>5,221.77</td>
      <td>17.18</td>
    </tr>
    <tr>
      <th>min</th>
      <td>81.00</td>
      <td>72.00</td>
      <td>35.00</td>
      <td>1.00</td>
      <td>9.00</td>
      <td>139.00</td>
      <td>1.00</td>
      <td>2,340.00</td>
      <td>1,780.00</td>
      <td>96.00</td>
      <td>250.00</td>
      <td>8.00</td>
      <td>24.00</td>
      <td>2.50</td>
      <td>0.00</td>
      <td>3,186.00</td>
      <td>10.00</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>776.00</td>
      <td>604.00</td>
      <td>242.00</td>
      <td>15.00</td>
      <td>41.00</td>
      <td>992.00</td>
      <td>95.00</td>
      <td>7,320.00</td>
      <td>3,597.00</td>
      <td>470.00</td>
      <td>850.00</td>
      <td>62.00</td>
      <td>71.00</td>
      <td>11.50</td>
      <td>13.00</td>
      <td>6,751.00</td>
      <td>53.00</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1,558.00</td>
      <td>1,110.00</td>
      <td>434.00</td>
      <td>23.00</td>
      <td>54.00</td>
      <td>1,707.00</td>
      <td>353.00</td>
      <td>9,990.00</td>
      <td>4,200.00</td>
      <td>500.00</td>
      <td>1,200.00</td>
      <td>75.00</td>
      <td>82.00</td>
      <td>13.60</td>
      <td>21.00</td>
      <td>8,377.00</td>
      <td>65.00</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>3,624.00</td>
      <td>2,424.00</td>
      <td>902.00</td>
      <td>35.00</td>
      <td>69.00</td>
      <td>4,005.00</td>
      <td>967.00</td>
      <td>12,925.00</td>
      <td>5,050.00</td>
      <td>600.00</td>
      <td>1,700.00</td>
      <td>85.00</td>
      <td>92.00</td>
      <td>16.50</td>
      <td>31.00</td>
      <td>10,830.00</td>
      <td>78.00</td>
    </tr>
    <tr>
      <th>max</th>
      <td>48,094.00</td>
      <td>26,330.00</td>
      <td>6,392.00</td>
      <td>96.00</td>
      <td>100.00</td>
      <td>31,643.00</td>
      <td>21,836.00</td>
      <td>21,700.00</td>
      <td>8,124.00</td>
      <td>2,340.00</td>
      <td>6,800.00</td>
      <td>103.00</td>
      <td>100.00</td>
      <td>39.80</td>
      <td>64.00</td>
      <td>56,233.00</td>
      <td>118.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
college.describe(include=['object'])
# or college.describe(include=['O'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Private</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>777</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>2</td>
    </tr>
    <tr>
      <th>top</th>
      <td>Yes</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>565</td>
    </tr>
  </tbody>
</table>
</div>



* [2] [http://stackoverflow.com/questions/24524104/pandas-describe-is-not-returning-summary-of-all-columns](http://pandas.pydata.org/pandas-docs/version/0.19.1/generated/pandas.DataFrame.describe.html)
* [3] [http://stackoverflow.com/questions/24524104/pandas-describe-is-not-returning-summary-of-all-columns](http://stackoverflow.com/questions/24524104/pandas-describe-is-not-returning-summary-of-all-columns)
* [4] [http://dataanalysispython.readthedocs.io/en/latest/pandas.html#summarizing-data-describe](http://dataanalysispython.readthedocs.io/en/latest/pandas.html)

## ii. Pair plot

Unlike R, seaborn does not pairplot categorical vs numerical. See more [here](https://github.com/mwaskom/seaborn/issues/919).


```python
g = sns.PairGrid(college, vars=college.iloc[:,1:11], hue='Private')
g.map_upper(plt.scatter, s=3)
g.map_diag(plt.hist)
g.map_lower(plt.scatter, s=3)
g.fig.set_size_inches(12, 12)
```


![png](02_08_files/02_08_16_0.png)


## iii. Box plots


```python
sns.boxplot(x='Private', y='Outstate', data=college);
```


![png](02_08_files/02_08_18_0.png)


## iv. Elite variable


```python
college.loc[college['Top10perc']>50, 'Elite'] = 'Yes'
college['Elite'] = college['Elite'].fillna('No')

sns.boxplot(x='Elite', y='Outstate', data=college);
```


![png](02_08_files/02_08_20_0.png)


## v. Histograms

In Python, to produce some histograms with differing numbers of bins for quantitative variables, we first need to convert these variables to bins.
When we create bins, we transform a continuous range of values into a discrete one. For the purposes of this exercise, we will only consider equal-width bins.


```python
# Bins creation
college['PhD'] = pd.cut(college['PhD'], 3, labels=['Low', 'Medium', 'High'])
college['Grad.Rate'] = pd.cut(college['Grad.Rate'], 5, labels=['Very low', 'Low', 'Medium', 'High', 'Very high'])
college['Books'] = pd.cut(college['Books'], 2, labels=['Low', 'High'])
college['Enroll'] = pd.cut(college['Enroll'], 4, labels=['Very low', 'Low', 'High', 'Very high'])
```


```python
# Plot histograms
fig = plt.figure()

plt.subplot(221)
college['PhD'].value_counts().plot(kind='bar', title = 'Private');
plt.subplot(222)
college['Grad.Rate'].value_counts().plot(kind='bar', title = 'Grad.Rate');
plt.subplot(223)
college['Books'].value_counts().plot(kind='bar', title = 'Books');
plt.subplot(224)
college['Enroll'].value_counts().plot(kind='bar', title = 'Enroll');

fig.subplots_adjust(hspace=1) # To add space between subplots
```


![png](02_08_files/02_08_24_0.png)


## vi. Continue exploring the data

"This exercise is [trivial](https://www.kaggle.com/pmarcelino/house-prices-advanced-regression-techniques/comprehensive-data-exploration-with-python) and is left to the reader." :)
