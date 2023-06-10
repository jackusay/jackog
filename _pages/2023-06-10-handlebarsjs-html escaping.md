## handlebarsjs Partials, html escaping

.hbs:
```
{{{content}}}
{{{address}}}
```

imgtxt.hbs:
```
<div class="row imgtxt">
  <div class="col-6"><img id="myImg" src="{{image}}" width="1024" height="576"></div> <!--src-->
  <div class="col-6"><p>{{txt}}</p></div> <!--txt-->
</div>
```

.js
```
var Handlebars = require('handlebars');
if (json.data.template == 'imgtxt') {
	json.data.content = fs.readFileSync('src/template/imgtxt.hbs', 'utf8').toString();
}

var tpl = Handlebars.compile(template);
var out = tpl(json.data);
// <p>I am a template!</p>
```

result:
html escaping {{{ }}} can insert html b, but b's {{ }} won't render.

imgtxt.vash part will show unrender {{txt}}.

solution:

use **partial** 

.hbs
```
{{#if imgtxt}}
  {{> imgtxt}}
{{/if}}
```

.js
```
if (json.data.template == 'imgtxt') {
	json.data.imgtxt = fs.readFileSync('src/template/imgtxt.hbs', 'utf8').toString();
	Handlebars.registerPartial('imgtxt', json.data.imgtxt);
}
```