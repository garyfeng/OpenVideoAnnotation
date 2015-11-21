# Gary's Notes on hacking OVA

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
