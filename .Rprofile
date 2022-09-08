cat("########################################################################################### 
    ############# Warning! git pull in this project is executed when R starts!#######################
    ##################################################################################################")

source("renv/activate.R")

renv::install(paste0(getwd(),"/Packages/papaja-devel.zip")) # there is need to not inclde papaja in renv file 
# renv::install("https://github.com/crsh/papaja/archive/refs/heads/devel.zip")

packages=c("psych","dplyr","lavaan","base","foreign",
           "Routliers","MVN","parameters", "EFA.MRFA","RGenData",
           "semPlot","psycho","apa","corx","effectsize","qwraps2",
           "finalfit","ggstatsplot","dunn.test","devtools","rticles",
           "ICC.Sample.Size","tidyverse","magrittr","osfr","expss",
           "gtsummary","huxtable","equaltestMI","haven","rcompanion",
           "ufs","semTools","semPlot","insight","xaringan","kableExtra","flextable",
           "lavaanPlot","DiagrammeRsvg","rsvg")


renv::install(packages)

renv::activate()
Sys.setenv(R_REMOTES_STANDALONE="true")
if(!"devtools" %in% rownames(installed.packages())) install.packages("devtools")
renv::install("https://cran.r-project.org/src/contrib/Archive/MissMech/MissMech_1.0.2.tar.gz")
library(MissMech)

renv::restore(prompt = F)

#################################################################xxxxxx[]
# if the function below is not functioning, it is neccessary to write into the console the two following commands: 
# 1. 
# in this command there is need to change user name in this case: lukas.novak
# system("git config --global user.name \"lukas.novak\"")

# 2. 
# in this command there is need to change user email adress in this case: lukasjirinovak@gmail.com
# system("git config --global user.email \"lukasjirinovak@gmail.com\"")

# auto_save_push = function(interval = 10) { # autosave of script and push every x(10) seconds
#   msg = timestamp(prefix = "Auto save ", suffix = "", quiet = T) # date and time 
#   cmd = sprintf("git commit -m\"%s\"",msg) # paste but into the CMD line - stinger can not be used 
#   invisible(rstudioapi::documentSave(rstudioapi::getActiveDocumentContext()$id)) # autosave of script
#   invisible(system("git pull",show.output.on.console = F)) 
#   invisible(system("git add --all",show.output.on.console = F))
#   invisible(system(cmd, show.output.on.console = F))
#   invisible(system("git push",show.output.on.console = F))
#   later::later(auto_save_push, interval) # loop 
# }


setHook("rstudio.sessionInit", function(newSession) {
  if (newSession)
    message("Welcome to Project template created by Lukas Novak")
  auto_save_push()
}, action = "append")

if (interactive() && requireNamespace("rsthemes", quietly = TRUE)) {
  if(!requireNamespace("suncalc", quietly = TRUE)) install.packages("suncalc")
  # Set preferred themes if not handled elsewhere..
  rsthemes::set_theme_light("Crimson Editor")  # light theme
  rsthemes::set_theme_dark("Vibrant Ink") # dark theme
  
  # Whenever the R session restarts inside RStudio...
  setHook("rstudio.sessionInit", function(isNewSession) {
    # Automatically choose the correct theme based on time of day
    rsthemes::use_theme_auto(lat = 50.197435, lon = 15.845782)
  }, action = "append")
}



# Stop, when pandoc is not present
{
  if (rmarkdown::pandoc_available()) 
  { 
    cat("Luckily, pandoc version", as.character(rmarkdown::pandoc_version()), "is available!\n") 
  }
  else { stop("There is need to instal pandoc 2.13 version! please instal it from: https://github.com/jgm/pandoc/releases/tag/2.13")}
}

# lapply(packages, library, character.only = TRUE) # for some reason this has to be off otherwise packages are loaded twice

# .Last <- function(){
#   (rmarkdown::pandoc_convert("IRI_validation.docx", to = "pdf", output = "IRI_validation.pdf"))
# }

# 
# .Last = function () {
#   if(length(list.files("C:/Program Files", "soffice.exe", recursive=TRUE,
#                        full.names=TRUE, include.dirs=TRUE)) == 0) { 
#     rmarkdown::pandoc_convert("IRI_validation.docx", to = "pdf", output = "IRI_validation.pdf")
#   } else
#   {
#     present.path <- paste0(getwd(),"/IRI_validation.docx")
#     
#     office.path <- list.files("C:/Program Files", "soffice.exe", recursive=TRUE,
#                               full.names=TRUE, include.dirs=TRUE)
#     # convert power-point to pdf
#     library(docxtractr)
#     convert_to_pdf(present.path,
#                    pdf_file = paste0(getwd(),"/IRI_validation.pdf"))
#   }
# }

# to active lazy git function, type the following into command line: 
# git config --global alias.lg '!f() { git add -A && git commit -m "$@" && git push; }; f'
# lazy git function is than activated using "git lg "commit massage" 
