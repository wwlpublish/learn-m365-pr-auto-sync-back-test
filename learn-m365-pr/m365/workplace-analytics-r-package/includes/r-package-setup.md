Do the following to set up the `wpa` R package:

1. Download and install the R software.
2. Install the `wpa` R package.
3. Load the `wpa` R package.

## 1. Download and install the R software

Go to [www.r-project.org](https://www.r-project.org), and when prompted, select the Comprehensive R Archive Network (CRAN) mirror, and then download and install R (open-source software).

The CRAN is a network of servers distributed around the world that are used to distribute R software and packages. Don't select a mirror that is close to you geographically. Instead, select the cloud mirror, which automatically detects the optimal mirror for you.

![Install R](../media/get-r.png)

You can also download and install an integrated development environment (IDE) to improve your programming experience. IDEs provide useful features such as code auto-complete, syntax checks, and viewing panels not available with a plain text notepad. RStudio is a commonly used IDE for R.

## 2. Install the `wpa` R package

Before you can use the `wpa` R package, you must do a one-time install of the package to ensure it is downloaded and set up on your computer. The `wpa` R package is available on the CRAN. To automatically install it, run the following in R:

```R
install.packages("`wpa`")
```

>[!IMPORTANT]
>As a best practice, restart your R session both before and after this installation.

The `wpa` package is dependent on other (multiple) R packages. When prompted to update the `wpa` package, you should update all on CRAN.

## 3. Load the `wpa` R package

Before you can use the `wpa` R package, you need to load the package at the beginning of each R session. Loading the package is analogous to installing and loading an app, except that it occurs within the R environment.

Each R package is stored in a directory called a library. After the installation is complete, run the following to load the `wpa` R package in your session:

```R
library(`wpa`)
```

>[!IMPORTANT]
>You only need to install the package one time. However, you will need to load it every time you start a new R session.

The `wpa` R package is designed to work with other R packages from Tidyverse. Tidyverse is a collection of R packages designed for data science. Generally, load `tidyverse` when you load `wpa`, as many of the examples for this learning path use the data manipulation and plotting functions from Tidyverse.

Run the following to install Tidyverse:

```R
install.packages("tidyverse")
```

## Create a script example

If you are new to using R, an easy way to learn it, is to try it for yourself. This example guides you through how to create a new script in R, write a short line of code, and view the output.

To complete the exercise:

1. Open R.
1. Select **File** > **New Script**.
1. Enter `print("Hello World!")`
1. Select **Ctrl**+**R** or select the button to **Run line or selection**.

![Create a script in R](../media/hello-world.png)

After you run the script, you'll be able to see the output in the console:

![Hello World output](../media/hello-world-2.png)

Now that you have downloaded and installed R and loaded the `wpa` R package, you are ready to analyze Workplace Analytics data. The `wpa` R package has multiple built-in sample datasets, including the `sq_data` person query output and the `mt_data` meeting query output. You'll see these sample datasets demonstrated in many of the `wpa` R package functions in the following units.

>[!IMPORTANT]
>Note that `sq_data` and `mt_data` are the names of demo datasets that are pre-loaded with the `wpa` R package. Avoid assigning demo dataset names to imported data, as it makes it easy to accidentally analyze the demo data instead of analyzing your imported dataset.

## Learn more

- [Download and install R](http://www.r-project.org)
- [Download and install RStudio Desktop](https://www.rstudio.com/products/rstudio/download)
- [Download an installation file and install it locally](https://github.com/microsoft/wpa/releases)
- [Learn more about Tidyverse](https://www.tidyverse.org)
- [`wpa` R package cheat sheet](https://github.com/microsoft/wpa/blob/main/man/figures/wpa%20cheatsheet.pdf)
