#
# library(devtools)
# library(roxygen2)
# library(usethis)
# # #install.packages("data.table")
# # #install.packages("data.table", repos="https://Rdatatable.gitlab.io/data.table")
# #
# library(data.table)
# library(seewave)
# library(signal)

##============================================

#Define all functions and then call them in the main file by source()
#use use_r from use this package

# use roxygen ==> go inside the function and then from menu --> code --> inser roxygen skeleton
#use_r("trunc")
# library(devtools)
# devtools::install

# if cant install, go to r studio settings and check R path#

# then add licence file like this use_cc0_license("Tomas Westlake")
# ?use_mit_license
# use_mit_license(name = c("Rubin","Javad Khataei","Beap Lab"))

# make document for whole package using this
# usethis::use_package_doc()
# Now try devtools::document() to see the changes made by roxygen
# devtools::document()



#add a logo
#use_logo("Z:/Research/dfuller/Walkabilly/people/Seyed Javad/Pack/BEAP_Lab_logo.png")

#add vignette by use_vignette("name_vignette")
#


# if a function is using a package you need to do 2 things
# 1 #' @import seewave (, signal )each is a seperate line) in the function file
# clean and build so it will be added to the namespace file
#
# 2 use use_package("name of the package") for each library
# check description file, now it has the libraries

# Note : if you want the external libraries got loaded when you packahe is loaded use Depend instead of import so
# use_package("seewave",type = "Depends")



#Note : after exporting each funtion use use_namespace to export the name of the functions so R can see your function to call

# refresh the document by devtools::document()





# ===================
# continuous integration
# travis, check the package for different operation systems(linux and mac) and R versions
# use github to log in

# then add read me file
# use_readme_rmd()
#later edit the readme file
# use_travis()


# it will add something like  this to readme.rmd file
#<!-- badges: start -->
# [![Travis build status](https://travis-ci.org/Javad-mun/rubin.svg?branch=master)](https://travis-ci.org/Javad-mun/rubin)
# <!-- badges: end -->

Now we can edit travis file and for example add the R versions like this:
r:
  - oldrel
  - release
  - devel
Also to run for both osx and linux go with
os:
  - linux
  - osx
  
Then Build and push. it will check all versions and os listed in yml file and even for warnings throews an error as warnings_are_errors: defualt value is true.

# for Windows use use_appveyor() which is simillar to travis

There are other options like rhub package which I try here :
https://r-hub.github.io/rhub/articles/rhub.html
After installing rhub, validate your email by rhub::validate_email(email ="example@a.ca"), (if error retart rstudio) then run
rhub::check() # now choose one os
also check https://r-hub.github.io/rhub/articles/rhub.html


=========
###to check the coverage instal covr and then use_coverage. it gives you some code to add to travis and it will add some info to read me
Now navigate to codecov.io and link the github repo to it.


=====
Testing, 
install tester and testthat packages.
then run use_testthat.  usethis::use_testthat()
it makes testthat.R and a folder and also adds a suggestion for testthat library to the description file.
we have a message the, ● Call `use_test()` to initialize a basic test file and open it for editing.

Now we run use_test(name="name_of_the_test_fiel")
and it will create a file inside the test/testthat folder and we can edit that and put the code there

We need to make a dataset and the expected output to check the code.


# Import data into the package
with use_data(nameofthedata, compress= "xz") we can include the data in the package. It will create a folder, data, and the data will be compressed and stored there.
the maximun for data size is 5 megabytes. "xz" can reduce a csv file size to 1/14. the "bzip2" compression method is stronger than "xz".the "gzip" is the weakest.
Note when data is added to the package, there is a dependency on R versions jigher than 2.10, therefore add Depends: R (>= 2.10) in the description file before the licence.



##
When writing vignette file, using mark down . you can use CSS code to style the document like this:
<style>
body{
text-align : justify;
line-height: 2em;
}
</style>

========
to add a help, documentation, file to the package itself, run
usethis::use_package_doc(). it will create a dummy R file and after doing devtoos::document(), roxygen will create an .Rd file for the package.
When writing the packge document, have a look at this link for more options: https://cran.r-project.org/web/packages/roxygen2/vignettes/rd.html
