# install java
brew update

brew tap adoptopenjdk/openjdk

brew search jdk

brew install --cask adoptopenjdk11

# check where java is installed
/usr/libexec/java_home -V

#
java --version

# install Nextflow
curl -fsSL get.nextflow.io | bash

mv /Users/steve/engene/pgsc_calc/nextflow ~

# Next, install Docker, Singularity, or Anaconda
### docker is already installed
nextflow run pgscatalog/pgsc_calc --help


# Calculate your first polygenic scores
nextflow run pgscatalog/pgsc_calc \
    -profile docker \
    --input samplesheet.csv --target_build GRCh37 \
    --pgs_id PGS001229

# How do I run the pipeline on an M1 Mac?

nextflow run pgscatalog/pgsc_calc \
    -profile docker,test \
    --platform arm64