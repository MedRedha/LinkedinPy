# LinkedinPy


## Installation:
It is recomended to use via pyenv We will be supporting python 3.6.0 and above going forward

```
pip install --upgrade pip
curl https://pyenv.run | bash
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
pyenv install 3.6.0
pyenv local 3.6.0
pip install -r requirements.txt
```

##  Interact APIs
  - [search and connect](#search-and-connect)
  - [connect from suggested](#connect-from-suggested)
  - [search and endorse](#search-and-endorse)
  - [withdraw old invitations](#withdraw-old-invitations)
  - [jobs easy apply](#jobs-easy-apply)
  - [auto reply messages with the first suggestion](#auto-reply-messages-with-the-first-suggestion)

##  Download APIs
  - [save 1st connects to db](#save-1st-connects-to-db)
  - [search 1st connects and save to db](#search-1st-connects-and-save-to-db)

### search and connect
 
It sends invite to your 2nd or 3rd degree connections fetched from linkedin search

```python
 session = LinkedinPy()

 with smart_run(session):
     session.search_and_connect(
                    query="founder",
                    connection_relationship_code="%5B%22S%22%5D",
                    city_code="%5B%22in%3A6508%22%5D",
                    school_code="%5B%2213497%22%5D"
                )
 ```

### connect from suggested

```python
 session = LinkedinPy()

 with smart_run(session):
     session.connect_from_suggested(titile_must_contain="founder")
```

### search and endorse

It simply endorses your first connections fetched from linkedin search

```python
 session = LinkedinPy()

 with smart_run(session):
     session.search_and_endorse(
                    query="founder",
                    city_code="%5B%22in%3A6508%22%5D",
                    school_code="%5B%2213497%22%5D"
                )
 ```

### withdraw old invitations

It's an API to withdraw invitation a month or more older
 
```python
 session = LinkedinPy()

 with smart_run(session):
    session.withdraw_old_invitations(skip_pages=5)
 ```

### jobs easy apply

It's an API to apply for jobs with "easy appy" button on linkedin
```python
 session = LinkedinPy()

 with smart_run(session):
    session.jobs_easy_apply(position = 'Engineering Manager', 
      location = 'United States',
      resumeloctn = '/Users/ishandutta2007/Downloads/IshanDutta.big.pdf',
      language='en',
      max_applications = 5)
 ```
 Options `resumeloctn`, `language` and `max_applications ` are `None`, `en` and `5` by default.
 Leave `resumeloctn` blank incase your linkedin profile already shows attached resume.

### auto reply messages with the first suggestion
For now the API just clicks the first suggestion for each of the messages, (Plans to integrate intelligence later. Use this with causion incase you want to, this was created just for fun)

```python
 session = LinkedinPy()

 with smart_run(session):
    session.auto_reply_messages_with_the_first_suggestion()
 ```


### save 1st connects to db

It's an API to backup already connected contacts to local DB(for old connections and connections not made through search_and_connect API)
 
```python
 session = LinkedinPy()

 with smart_run(session):
     session.save_1stconnects_todb(
                    skip_scrolls=5,
                    tot_scrolls=10
                )
 ```

### search 1st connects and save to db

It's an API to backup already connected contacts to local DB(for old connections and connections not made through search_and_connect API)
 
```python
 session = LinkedinPy()

 with smart_run(session):
     session.search_1stconnects_and_savetodb(
                    query="founder",
                    city_code="%5B%22in%3A6508%22%5D",
                    school_code="%5B%2213497%22%5D"
                )
 ```

## How to run:

 -  modify `quickstart.py` according to your requirements
 -  `python quickstart.py -u <my_linkedin_username> -p <mypssword>`

## How to schedule as a job:

```bash
    */10 * * * * bash /path/to/LinkedinPy/run_linkedinpy_only_once_for_mac.sh /path/to/LinkedinPy/quickstart.py $USERNAME $PASSWORD
```


## Help build socialbotspy
Check out this short guide on [how to start contributing!](https://github.com/InstaPy/instapy-docs/blob/master/CONTRIBUTORS.md).

