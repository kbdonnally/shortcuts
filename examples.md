# Examples

Pasting from Workflows so that I can delete them. (Keeping some around that I never use because I wanna know how they work.)

### 1. Edit Webpage
- Is just this one JS command
- Run with Share Sheet in browser and you can edit the rich text of the webpage like you would a Word document
	
```javascript
document.body.contentEditable = "true";
document.designMode = "on";

completion();
```

### 2. Find Emails On Webpage

- Again, just a JS command
- This shortcut sets you up with an email to send to all the addresses on the page, but you could easily save them as a list, or to contacts, or whatever you needed them for
- To use the output, the variable is `JavaScript Result` (as Dictionary... can be lots of diff var types apparently)
	- *How does apple know to split the dictionary when it's setting up the email?*

```javascript
function removePrefixFromString(prefix, string) {
	var firstIndex = string.indexOf(prefix);
	if (firstIndex < 0) {
		return string;
	}

	return string.substring(firstIndex + prefix.length);
}

var links = document.querySelectorAll("a");
var emails = [];
for (var link of links) {
	var href = link.getAttribute("href") || "";
	const mailtoScheme = "mailto:";
	const slashesFromScheme = "//";

   if (!href.startsWith(mailtoScheme)) {
      continue;
   }

	var email = removePrefixFromString(mailtoScheme, href);
	email = removePrefixFromString(slashesFromScheme, email);

   // Don't add duplicates
	if (emails.indexOf(email) === -1) {
		emails.push(email);
	}
}

completion(emails);
```

*NB: Ohhh! So this must be what the "completion" variable does! You can feed yourself a result this way. Cool!*
