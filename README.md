# Automatic RoamResearch backup

This script help you backup your [RoamResearch](roamresearch.com)!

This script automatically
- Download a markdown archive of your RoamResearch workspace
- Download a json archive of your RoamResearch workspace
- Unzip them to your git directory
- Commit and push the difference

# Why to use it

- You have a backup if RoamResearch lose some of your data.
- You have a history of your notes.
- You can browse your Github repository with a mobile phone.

# How to use it

## Setup

- Clone this repository locally: `git clone https://github.com/MatthieuBizien/roam_research_download.git`
- [Create a (private) Github repository for all your notes](https://help.github.com/en/github/getting-started-with-github/create-a-repo)
- Clone it into a `notes/` directory,
at the root of this repository. 
`git clone git@github.com:GITHUB_USERNAME/GITHUB_REPO notes`
- Create a `.env` file for storing your secrets (RoamResearch email and password):
`cp env.template .env`
- Fill the .env file: `vi .env`
- Create a [conda](https://www.anaconda.com/) environment: `conda env create -f environment.yml`
(you can of course use stock Python, but python 3.6 is required)

## Manual backup

- Activate the conda environment: `conda activate roam_research_download`
- Run the script: `./rr_download.py`
- Check your Github repository, it should be filled with your notes :)

## Automatic backup

One-liner to run it with a [cron](https://en.wikipedia.org/wiki/Cron) every hours: 
`conda activate roam_research_download && echo "0 *  *  *  *  PATH=$(dirname $(which python)):\$PATH '$(pwd)/rr_download.py'" | crontab -`

# Task list

- [x] Download automatically from RoamResearch
- [x] Push it to Github
- [x] Create Cron
- [x] Write detailed README
- [x] Publish the repository on Github
- [ ] Format Markdown notes to be more readable on Github
- [ ] Add backlinks
- [ ] Add automatic Google Keep retrieval
