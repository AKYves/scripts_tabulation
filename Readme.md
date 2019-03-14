
## Introduction

For those wanting a fine and more interesting control on the output aspect,
I am working on a package which will probably improve enough this project,
with more themes and more options for the final output. 
I didn't delete this project to let know about the origin ideas at the birth of
the package. Please, you
could take a look on [tabuldevr](//github.com/AKYves/tabuldevr.git)

The purpose of this folder is to create a list of tables
and table names and send them to an excel sheet. The goal is to come up
easily with deliverables after a survey.

I believe in reproductible research, so if you want to have your analysis and 
your comments in the same report, please consider Rmarkdown.

The functions are mainly based on the great package [openxlsx](//github.com/awalker89/openxlsx).

---

## Demo


We assume that you just want the tables of your survey divided in 
three sections:

- Section One
- Section Two
- Section Three


```r
if(!require(openxlsx)) install.packages("openxlsx")
source("functions_tabulations.R")


#one section per sheet
sheet_names <- c("section_one",
                "section_two",
                "section_three"
)

# The header name of each of the sheets
header_names <- c("Tables of Section One: MTCARS & TITANIC",
                "Tables of Section Two",
                "Tables of Section Three"
)

#You initiate here your workbook
wb <- initiate_workbook(sheet_names, header_names)

##... You do a lot of stuffs and you generetate tables (actually dataframes).
## You can put all the dataframes and their names in two lists of same length


TABLES_LIST <- list(mtcars = mtcars,
                    dnase = DNase
)

NAMES_LIST <- list(mtcars = "Table One - Mtcars Data",
                   dnase = "Table Two - Elisa assay of DNase" 
)

#You push the data frame and the list in one spread sheet.
#from the function available in functions_tabulations.R
push_all_tables(wb, 
                listoftables = TABLES_LIST,
                listofnames = NAMES_LIST,
                sheetname = "section_one"
)

#You do your stuffs and the same thing for anoter sheet if you want...


#You save your workbook and that is!
saveWorkbook(wb, file = "demo.xlsx",
             overwrite = TRUE)
```

Please feel free to add you inputs. It is just a little file for those in hurry

## Licence
MIT
