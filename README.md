# Answers

1. `SELECT salary FROM emp WHERE Emp_ID = "273407"`

   - 110241

2. `SELECT First_Name FROM emp WHERE City = "Palo Alto" AND Gender = "F"`

   - Dawne

3. `SELECT First_Name, Last_Name, Years_in_Company FROM emp order by Years_in_Company DESC limit 1`

   - Otha Orrell

4. `SELECT First_Name , Last_Name , Age_in_Years , City , State FROM emp WHERE First_Name = "Jack"`

   - Jack Warfel 49.62 El Paso TX
   - Jack Fujita 24.1 Pineville SC,
   - Jack Hackney 28.92 Brooklyn NY
   - Jack Jacobson 59.37 Rockholds KY

5. `SELECT * FROM emp WHERE First_Name LIKE "J%" AND Age_in_Years > 55 AND Gender "F" AND E_mail LIKE "%gmail%"`

   - 193333 Ms. Jesica D Stackpole F jesica.stackpole@gmail.com Corey Stackpole Shela Stackpole Miramontes 12/16/1957 1:31:59 PM 59.65 43 11/1/1981 Q4 H2 1981 11 November Nov 1 Sunday Sun 35.76 102380 14% 250-99-4920 212-322-9444 Staten Island Richmond Staten Island NY 10307 Northeast
   - 207021 Ms. Jewell B Charon F jewell.charon@gmail.com Deandre Charon Carri Charon Mask 10/26/1960 12:30:22 PM 56.79 58 1/11/2001 Q1 H1 2001 1 January Jan 11 Thursday Thu 16.55 83536 11% 209-84-6241 217-977-5144 Vergennes Jackson Vergennes IL 62994 Midwest
   - 424237 Ms. Jeanette P Huie F jeanette.huie@gmail.com Arthur Huie Alecia Huie Brunk 8/31/1957 2:16:56 AM 59.95 54 3/28/2007 Q1 H1 2007 3 March Mar 28 Wednesday Wed 10.34 62400 12% 150-23-5541 210-776-4590 Rusk Cherokee Rusk TX 75785 South
   - 310324 Ms. Julee M Jain F julee.jain@gmail.com Rolf Jain Cindy Jain Goforth 4/28/1959 1:50:14 AM 58.29 48 8/5/2003 Q3 H2 2003 8 August Aug 5 Tuesday Tue 13.99 105695 3% 654-38-2788 202-231-9433 Washington District of Columbia Washington DC 20370 South
   - 423112 Ms. Janet L Tindal F janet.tindal@gmail.com Leigh Tindal Rochell Tindal Badger 3/23/1962 1:24:43 AM 55.39 48 3/26/1991 Q1 H1 1991 3 March Mar 26 Tuesday Tue 26.36 45059 27% 440-29-0024 219-503-5670 Colfax Clinton Colfax IN 46035 Midwest
   - 203864 Mrs. Jodi R Hattaway F jodi.hattaway@gmail.com Travis Hattaway Youlanda Hattaway Dison 7/19/1958 8:17:20 AM 59.07 58 10/19/1994 Q4 H2 1994 10 October Oct 19 Wednesday Wed 22.79 104803 22% 245-99-9444 252-777-5856 Avon Dare Avon NC 27915 South
   - 522783 Mrs. Jada F Dorr F jada.dorr@gmail.com Quinton Dorr Arianna Dorr Gainer 10/22/1959 5:25:37 PM 57.81 44 11/12/1992 Q4 H2 1992 11 November Nov 12 Thursday Thu 24.72 195696 21% 516-49-9538 239-820-5728 Maitland Orange Maitland FL 32751 South
   - 328252 Hon. Jacquie B Dillinger F jacquie.dillinger@gmail.com Curt Dillinger Lynell Dillinger Bently 7/5/1959 4:53:46 PM 58.1 57 8/10/2002 Q3 H2 2002 8 August Aug 10 Saturday Sat 14.98 122164 5% 360-08-1142 406-982-9583 Avon Powell Avon MT 59713 West
   - 639430 Mrs. Jerry C Ingersoll F jerry.ingersoll@gmail.com Lyman Ingersoll Antonia Ingersoll Gilley 6/8/1962 6:53:24 AM 55.18 41 6/6/2011 Q2 H1 2011 6 June Jun 6 Monday Mon 6.15 138860 5% 428-99-6584 201-605-3884 Hawthorne Passaic Hawthorne NJ 7507 Northeast
   - 281263 Hon. Junko Q Babin F junko.babin@gmail.com Bud Babin Hellen Babin Pough 7/9/1960 7:45:04 PM 57.09 50 9/28/1987 Q3 H2 1987 9 September Sep 28 Monday Mon 29.85 128696 6% 323-11-4743 219-608-4244 Chalmers White Chalmers IN 47929 Midwest

6. `SELECT First_Name , Last_Name , Age_in_Years , City , State FROM emp WHERE Age_in_Years > 50 AND First_Name LIKE "J%" AND Gender = "M" AND State = "IL"`

   - Julio Swafford 55.25 Springfield IL
   - Jarod Parkes 58.1 Walnut Hill IL
   - Julio Thurlow 50.12 Rockford IL

7. `SELECT First_Name , Last_Name , salary, City , State FROM emp WHERE Age_in_Years > 50 AND Fathers_Name LIKE "%J%" AND salary > 100000 AND State = "NY"`

   - Cordell Tweedy 184326 Bronx NY
   - Moises Bill 131927 Tyrone NY
   - German Overbey 185583 Stormville NY
   - Marlon Encarnacion 195389 Durhamville NY

8. `SELECT First_Name, Last_Name, Gender, Age_in_Years, salary, City, State FROM emp WHERE (Age_in_Years > 50 OR Age_in_Years < 30) AND Gender = "F" AND Last_Name LIKE "B%" AND salary > 80000 AND State = "NY"`

   - Bernarda Bristow F 50.25 83235 Warrensburg NY
   - Paula Beverly F 29.61 160002 Plainville NY
   - Becki Bissonette F 50.98 193436 Port Washington NY
   - Meagan Borkholder F 26.2 145532 Cassville NY
   - Minh Bella F 24.03 143444 New Rochelle NY
   - Gladys Bouldin F 55.65 124213 Elizabethtown NY
   - Kristle Boots F 23.08 88783 Forestburgh NY
   - Mertie Buffum F 55.07 177846 Lake George NY
   - Tena Belote F 58.86 143846 Purdys NY

9. `SELECT First_Name, Last_Name, Gender FROM emp WHERE GENDER = "F" AND First_Name = any(SELECT First_Name FROM emp WHERE Gender = "M")`

   - ...164 results

10. `SELECT First_Name, Last_Name, Gender, salary, Age_in_Years FROM emp WHERE Last_Name = any(SELECT Last_Name FROM emp WHERE salary > 70000)`

    - ...4,653 results

11. `SELECT First_Name, Last_Name, Gender, salary, Age_in_Years FROM emp WHERE First_Name LIKE "_____" AND Last_Name = any(SELECT Last_Name FROM emp WHERE Years_in_Company > 5)`

    - ...827 results

12. `SELECT first_name,last_name,age_in_years, CASE WHEN age_in_years < 30 THEN "young" WHEN(age_in_years > 30 OR age_in_years < 50) THEN "adult" WHEN age_in_years > 50 THEN "old" END AS "physical condition" FROM emp`

    - ...5,417 results

13. `SELECT first_name, last_name, Years_in_Company, name_prefix, CASE WHEN Years_in_Company < 5 THEN "Young" WHEN(Years_in_Company < 15 AND Years_in_Company > 5) THEN "Expirienced" WHEN Years_in_Company > 15 AND name_prefix in ("Prof.", "Drs.", "Dr.") THEN "Expert" ELSE "Super Expert" END AS "PAZAM" FROM emp ORDER BY Years_in_Company`

    - ...5,417 results

14. `SELECT first_name, last_name FROM emp ORDER BY First_Name ASC, Last_Name ASC`

    - Aaron Holquin
    - Aaron Maclennan
    - Aaron Takahashi
    - Abdul Bueno
    - Abe Bettencourt
    - Abe Macleod
    - Abe Paro
    - ...5,417 results

15. `SELECT first_name, last_name, Weight_in_kgs, Age_in_Years FROM emp ORDER BY Weight_in_kgs ASC, Age_in_Years DESC`

    - Angelita Boswell 40 59.96
    - Lorri Ziemba 40 59.47
    - Asuncion Braunstein 40 59.25
    - Amelia Crigler 40 59.21
    - ...5,417 results
