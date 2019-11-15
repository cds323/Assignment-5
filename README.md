# Doing a timed read of the same file with fread()
### Run as a block of text to time #########
ptm <- proc.time()
DF <- fread("UNRATE.csv", header="auto", 
            data.table=FALSE)
FREAD_READ_TIME <- (proc.time() - ptm)
FREAD_READ_TIME
############################################

# Examining what we got
class(DF)
typeof(DF)
str(DF)
names(DF)

# Bringing in column headers as names and using them to set names
### Run as a block of text to time #########
ptm <- proc.time()
header <- read.table("UNRATE.csv", header = TRUE,
                     sep=",", nrow = 1)
DF <- fread("UNRATE.csv", skip=1, sep=",",
                  header=FALSE, data.table=FALSE)
setnames(DF, colnames(header))
rm(header)
FREAD_READ_TIME <- (proc.time() - ptm)
FREAD_READ_TIME
############################################


