For example, I have chapters audio files for a book.

1. Add → Folder → Add folder.
2. If audio files alright have title → Chapters → Chapter 1 → Edit
	 - "Chapter" (Off)
	 - Chapter No (Off) `title`
	 - Duration (Off)
	 - Apply for all chapters (On)
3. If not have, Chapter 1 → Edit → Enter `custom title`. Do it for every chapters.
4. Edit `Book Info`.
5. Go tab `Art Work`, Add the cover picture.
6. Quality:
	 ```
	 Preset: android 5+
	 Format: m4b
	 Split by: parts
	 Speed: 1.0
	 Sampling frequency, Hz: 44100
	 Channels: 2
	 Cut-off frequencies higher than: 12000
	 Force re-encoding: Auto
	 Constant bitrate, kb/s: 128
	 ```
7. Start.

## Name template

Book filename teamplate:

```
<WRITER><if(SERIES)> - <SERIES><if(BOOK_NUMBER)> - Book <BOOK_NUMBER; format="%,02d"><endif><endif> - <TITLE><if(NARRATOR)> {<NARRATOR>}<endif>
```

Book Part filename template (Default):

```
<if(WRITER)><WRITER> <endif><if(SERIES)>- [<SERIES><if(BOOK_NUMBER)> -<BOOK_NUMBER><endif>] - <endif><if(TITLE)><TITLE><endif><if(NARRATOR)> (<NARRATOR>)<endif><if(YEAR)>-<YEAR><endif><if(PART)>, Part <PART; format="%,03d"><endif>
```

Chapter template (Default):

```
<if(BOOK_NUMBER)><BOOK_NUMBER>. <endif><if(BOOK_TITLE)><BOOK_TITLE>. <endif><if(CHAPTER_TEXT)><CHAPTER_TEXT> <endif><if(CHAPTER_NUMBER)><CHAPTER_NUMBER; format="%,03d"> <endif><if(TAG)><TAG> <endif><if(CUSTOM_TITLE)><CUSTOM_TITLE> <endif><if(DURATION)> - <DURATION; format="%02d:%02d:%02d"><endif>
```