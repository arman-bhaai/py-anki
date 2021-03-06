> ### "اعوذ بالله من الشیطان الرجیم"
> ### "I seek refuge in Allah from shaitan, the accursed one."
 
> ## "بسم الله الرحمن الرحيم"
> ## "In the name of Allah, the Most Gracious, the Most Merciful."
 
> # "إياك نعبد و إياك نستعين"
> # "It is You we worship and You we ask for help."
> ## [*- Al Fatihah : 05*](https://quran.com/1/5?translations=20)
<br>
<br>
 
# **Py-Anki**
* ### *Package Name* ---> **Py-Anki**
* ### *Package Description* ---> A simple API for Anki Spaced Repetition
* ### *Package URL* ---> **https://pypi.org/project/py-anki/#files**
* ### *Developed By* ---> **[#arman_bhaai](https://www.google.com/search?q=%23arman_bhaai&oq=%23arman_bhaai)** *(either click on this hashtag or make a google search to discover more about my works)*
* ### *My Personal Portfolio* ---> **https://arman-bhaai.github.io** *(some of my great projects are listed on my portfolio, so make sure you went through this)*
* ### *Find Me on Github* ---> **https://github.com/arman-bhaai**
* ### *Find Me on Facebook* ---> **[fb.me/arman.bhaai](https://www.facebook.com/arman.bhaai)**
<br>
<br>

## About
---
Py-Anki is an unofficial python binding/wrapper for [AnkiConnect](https://github.com/FooSoft/anki-connect) RESTful API. You can control all your Anki actions (eg: Create Deck, Add Notes, Get Card Info) using this package, in a more pythonic way.
<br>
<br>

# **Documentation**
## Warning : This package is under development yet.
<br>

## Steps to use the API
---
* First of all you need to install [AnkiConnect](https://ankiweb.net/shared/info/2055492159) addon on your Anki Software. 
* Then, run Anki Software and switch to your desired profile.
* Now run the example codes mentioned below...


## Examples
---
* ## Create Deck 
  <br>

  ```python
  # import api class from py-anki package
  from py_anki import AnkiApi

  # create an instance of the api class
  anki = AnkiApi()

  # store deck creation query
  deck = anki.create_deck('New Deck')

  # execute the query
  anki.exec(deck)
  ```
  Expected Result : 
  <br>
  <br>
  <img src="docs/create-deck.png" width="70%" height="70%">
  <br>
  <br>
* ## Create Model / Note Type
  <br>

  ```python
  # import api class from py-anki package
  from py_anki import AnkiApi

  # create an instance of the api class
  anki = AnkiApi()

  # store model creation query
  model = anki.create_model('New Model')

  # execute the query
  anki.exec(model)
  ```
  Expected Result : 
  <br>
  <br>
  <img src="https://raw.githubusercontent.com/arman-bhaai/py-anki/main/docs/create-model.png" width="70%" height="70%">
  <br>
  <br>


* ## Create Single Note
  <br>

  ```python
  # import api class from py-anki package
  from py_anki import AnkiApi

  # create an instance of the api class
  anki = AnkiApi()

  # populate note fields
  field1 = 'What is your name?' # for Front field
  field2 = 'arman_bhaai'
  note_fields = [field1,field2]

  # store note creation query
  note = anki.create_note(note_fields, deck_name='New Deck', model_name='New Model')

  # execute the query
  anki.exec(note)
  ```
    Expected Result : 
  <br>
  <br>
  <img src="https://raw.githubusercontent.com/arman-bhaai/py-anki/main/docs/create-note.png" width="70%" height="70%">
  <br>
  <br>
  <img src="https://raw.githubusercontent.com/arman-bhaai/py-anki/main/docs/create-note-2.png" width="70%" height="70%">
  <br>
  <br>

* ## Create Multiple Notes with Media
  <br>

  ```python
  # import api class from py-anki package
  from py_anki import AnkiApi

  # create an instance of the api class
  anki = AnkiApi()

  # store picture from the web for Note 1
  note1_picture = anki.fetch_picture(
    url='https://images.all-free-download.com/images/graphiclarge/beautiful_flower_series_04_hd_pictures_166886.jpg', 
    filename='flower_jasmin.jpg',
    fields=['Front, Back']
  )

  # store audio from the web for Note 1
  note1_audio1 = anki.fetch_audio(
    url='https://lex-audio.useremarkable.com/mp3/jasmine_us_1.mp3', 
    filename='pronunc_jasmine.mp3', 
    fields=['Back']
  )
  
  # store another audio from the web for Note 1
  note1_audio2 = anki.fetch_picture(
    url='https://lex-audio.useremarkable.com/mp3/flower_us_1.mp3',
    filename='pronounc_flower.mp3',
    fields=['Back']
  )
  note1 = anki.create_note(
    field_vals=['What is the name of this flower?', 'Jasmine'],
    deck_name='Default',
    model_name='Basic',
    audios=[note1_audio1, note1_audio2],
    pictures=[note1_picture],
    making_note_list=True
  )
  
  # store picture from the web for Note 2
  note2_picture = anki.fetch_picture(
    url='https://upload.wikimedia.org/wikipedia/commons/a/a6/Green_dome%2C_Masjid_e_Nabawi%2C_Medina%2C_KSA.jpg', 
    filename='masjid-e-nawawi.jpg',
    fields=['Front']
  )

  # store audio from the web for Note 2
  note2_audio1 = anki.fetch_audio(
    url='https://lex-audio.useremarkable.com/mp3/medina_1_us_2.mp3', 
    filename='pronunc_medina.mp3', 
    fields=['Back']
  )

  # store note with populated fields and media
  note2 = anki.create_note(
    field_vals=['Masjid e Nawawi is located in?', 'Medina'],
    deck_name='Default',
    model_name='Basic',
    audios=[note2_audio1],
    pictures=[note2_picture],
    making_note_list=True
  )

  # store list of notes
  notes = anki.create_notes([note1, note2])

  # execute the query
  anki.exec(notes)
  ```
    Expected Result : 
  <br>
  <br>
  <img src="https://raw.githubusercontent.com/arman-bhaai/py-anki/main/docs/create-multiple-notes-1.png" width="70%" height="70%">
  <br>
  <br>
  <img src="https://raw.githubusercontent.com/arman-bhaai/py-anki/main/docs/create-multiple-notes-2.png" width="70%" height="70%">
  <br>
  <br>
  <img src="https://raw.githubusercontent.com/arman-bhaai/py-anki/main/docs/create-multiple-notes-3.png" width="70%" height="70%">
  <br>
  <br>
<br>

# **Class Reference** (More to be added later...)
<br>

```python
### Class (* -> required)
AnkiApi(host:str, port:str)


  ### Attributes (Public)
  host:str

  port:str

  ### Methods (Public)
  create_model(*model_name:str, *in_order_model_fields:list, card_name:str, model_css:str, template_front:str, template_back:str) -> dict

  create_deck(*deck_name:str) -> dict

  fetch_picture(*url:str, *filename:str, fields:list) -> dict

  fetch_audio(*url:str, *filename:str, fields:list) -> dict

  create_note(*field_vals:list, deck_name:str, model_name:str, allow_duplicate:bool, tags:list, audios:list, making_note_list:bool) -> dict

  create_notes(*notes:list) -> dict

  exec(req_query:dict) -> json_obj

  ### Methods (Private)
  _find_model_fields_by_name(*model_name:str) -> list

  _catch_error(*json_resp:json_obj)
```