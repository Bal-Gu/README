# :warning: Before reading this make sure to be in a proper editor that supports MD files. Otherwise pictures won't load properly. 

![test](.\README_Images\test.PNG) 



In case you can't see the picture  and see `:warning:`above **and** you are in a proper editor make sure to:

1. Either change the `\` to `/` (if you aren't on windows)
2. Or view it online [here](https://github.com/Bal-Gu/README/tree/main/JAVA%20EE%20ex%202)



# How to run

````
mvn clean
mvn compile
mvn wildfly:deploy
//open your webbrowser with http://localhost:8080/stats
````



# Added Dependency

Two dependency have been added to maven.

1. OpenCSV a simple library to parse CSV files.
2. PrimeFace which helped to implement the charts and the table

# Useful commands to help you  test the program

### Requirements

#### xxxx-xxxx format

Provide a Date: `2003-2005`

Sector (click on it): `Construction` (or anything else)

````
//Output
    Starting date: 1-2003
    Ending date: 4-2005
    Sector: Construction 
````



#### xxxx-x-xxxx format

Provide a Date: `2003-3-2005`

Sector (click on it): `Construction` (or anything else)

````
//Output
    Starting date: 1-2003
    Ending date: 3-2005
    Sector: Construction 
````



#### x-xxxx-xxxx format

Provide a Date: `2-2003-2005`

Sector (click on it): `Construction` (or anything else)

````
//Output
    Starting date: 2-2003
    Ending date: 4-2005
    Sector: Construction 
````



#### x-xxxx-x-xxxx format

Provide a Date: `2-2003-3-2005`

Sector (click on it): `Construction` (or anything else)

````
//Output
    Starting date: 2-2003
    Ending date: 3-2005
    Sector: Construction 
````



#### multiple selection

Provide a Date: `2-2003-3-2005`

Sector (click on it): `Construction "Wholesale, transportation, accomodation and food service activities"` (or anything else)

````
//Output
    Starting date: 2-2003
    Ending date: 3-2005
    Sector: Construction Transports
````



Or if you want to go for the them all you can press the selectionbox on top  which will select them all.



````
//Output
    Starting date: 2-2003
    Ending date: 3-2005
    Sector: Industry Construction Transports Information Finance Specialized Administration others 
````



#### max upper range

Provide a Date: `2020-2021`

Sector (click on it): select the first one to  select them all

````
//Output
    Starting date: 1-2020
    Ending date: 2-2020
    Sector: Industry Construction Transports Information Finance Specialized Administration others 
````



Here the upper limit is capped since we don't have more data available.

**However** if the provided data is after 2021 the regex will catch it and not let the user validate the input even if the previous date are correct

#### date out of range

Provide a Date: `2021-2022`

Sector (click on it): select the first one to  select them all

[See output here on point 2.](#Highlight-of-some-features)

#### Wrong input

Provide a Date: `122222222222 `

Sector (click on it): select the first one to  select them all

[See output here on point 2.](#Highlight-of-some-features)

#### No input on sectors

Provide a Date: ` `

Sector (click on it): select the first one to  select them all

[See output here on point 4.](#Highlight-of-some-features)





# Highlight of some features

1. If nothing is entered in the secotr section either others or the previous selection will be taken again.

2. On a wrong date an error will pop up when hitting safe
   ![Fullscreen](.\README_Images\wrong format.PNG)

3. From the screenshot above we can also see that there is a dynamic error symbol that will show up if the format isn't right and if someone hit's safe nothing will happen. 

4. If there has been no date entered an explicit error will show up.

   ![Fullscreen](.\README_Images\empty.PNG)

5. If a date like `2005-2003` is provided the code will turn it in the right way and transform it into `2003-2005`![MaxBeforMin](.\README_Images\MaxBeforMin.PNG)



Here we can see that the starting date is then at 1-2003 even-though 2003 is after the `-`.

6. In case you want to know in the which column we currently are and the exact number of a bar you can hover over it.

   ![balken](.\README_Images\balken.PNG)

   

7. When having a lot of different bars the corresponding colors can be found on the right side of the screen.

   ![legendColors](.\README_Images\legendColors.PNG)

8. The lowest point of the graph starts from the minimum of all the values. This makes the chart have a bigger impact. It stops at the maximum on the top.

# :warning:Things to avoid :warning:

* Having the window not in full screen. This is how it should look like in full-screen. Sadly I didn't managed to fit the CSS in a proper way to make work on all resolutions. My screen resolution is 1920x1080 but anything higher should also work.

![Fullscreen](.\README_Images\Fullscreen.PNG)



* Taking a range that is too wide.

![Fullscreen](.\README_Images\ToWide.PNG)

While it technically  works to have the minimum of 1995 to 2-2020 it's not recommanded to use it for readability purposes of the graph. The lables underneath will overlap and without overwritting some part of the API itself to show verticialy it couldn't have been done.

* Taking to many sectors on a to small range

![towide2](.\README_Images\towide2.PNG)

Similar as above it wil make the data nearly unreadable. While it is working it's not recommanded to use it

![smallrangeRespected](.\README_Images\smallrangeRespected.PNG)

But as you can see here smaller ranges will make it work just fine.