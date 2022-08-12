# Updating R with installr
[Blog source](https://www.r-statistics.com/2015/06/a-step-by-step-screenshots-tutorial-for-upgrading-r-on-windows/)

For Windows 10

1. Open your old version of R (not RStudio)-If you don't remember where it is, click on the magnifying glass icon next to the windows icon on your task bar and simply type "R".
2. You'll be taking to the R console (the boring-looking one). Since you probably do not have installr , you may need to install it:
```
install.packages("installr")
library(installr)
updateR()
```
3. From there, just follow the instructions in the blog and voila!