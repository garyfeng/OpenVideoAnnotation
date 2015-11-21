# Gary's Notes on hacking OVA

by @garyfeng

----

# To-dos

- [X] HTML5/javascript only
- [x] Can load arbitrary videos from local [untested], URLs [yes], and youtube [yes]
- [x] Support time-based annotation [yes] with flexible interface [yes, showing richtext editor]
- [x] Annotations goes to a separate data server [yes, using any open annotation store]
- [x] Open source [yes, including the annotation store server side]

- [ ] Plan now to integrate this with the AMTurk workflow, e.g., generating unique URLs that automatically encode the video source and turker id
- [ ] Supporting thin-slicing: e.g. using https://github.com/cladera/videojs-offset
- [ ] Set up our own Annotation Store server: https://github.com/openannotation/annotator/wiki#backend-stores
- [ ] Replace the richtext editor with a websurvey like interface for quick rating
- [ ] tablet support [not yet due to a bug in videoJS]

## 2015-11-21: do I need an annotation store server

Or should I simply use AnnotateIt instead? See http://docs.annotatorjs.org/en/v1.2.x/authentication.html

## 2015-11-21: Creating the project page

Took some pains to create the http://garyfeng.github.io site.

Also added the following testing link: http://garyfeng.github.io/videoAnn/index.html

## 2015-11-20: Making `youtube.html`

Made an example for youtube annotation. From `demo.html`, got rid off the other videos,
and replaced the video with a presentation video.

The interface works well enough, although for youbute video player the coding interface
doesn't automatically show up with mouse over; you have to click on the video.

Also the `o` key is supposed to insert an annotation. It sometimes work and sometimes
doesn't. Not sure why.

- [ ] Need to simplify the rich text editor; no rich text, auto focus without clicking on it.
- [ ] Can we load a simple HTML survey question set
- [ ] Keyboard shortcuts for quick coding?

## 2015-11-20: Annotation data structure

Added the following line in `src\ova.js` line `528`

```
// garyfeng: debug: show all annotations
console.log(JSON.stringify(allannotations))
```
It turns out the annotation is an array of the following elements:

```
{
  "media":"video",
  "text":"<p>sdfsdf</p>",
  "ranges":[],
  "deleted":false,
  "uri":"http://danielcebrian.com/annotations/demo.html",
  "id":45,
  "archived":false,
  "created":"2015-11-21T03:48:53+0000",
  "updated":"2015-11-21T03:48:53+0000",
  "priority":"0",
  "imagePreview":"",
  "target":{
    "container":"vid3",
    "ext":"Youtube",
    "src":"https://www.youtube.com/watch?v=7aOByepu9_4"
    },
  "rangeTime":{"start":274.67781,"end":274.67781},
  "quote":"",
  "highlights":[]
}
```
