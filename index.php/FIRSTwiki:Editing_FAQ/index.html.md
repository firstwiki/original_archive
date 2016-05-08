# FIRSTwiki:How does one edit a page

## From FIRSTwiki

(Redirected from [FIRSTwiki:Editing FAQ](/index.php?title=FIRSTwiki:Editing_FAQ&redirect=no "FIRSTwiki:Editing
FAQ"))

Jump to: navigation, search

**[Community Portal](FIRSTwiki:Community_portal "FIRSTwiki:Community portal")**

- **[Help page](FIRSTwiki:Help "FIRSTwiki:Help")**
- [New users page](FIRSTwiki:New_users_page "FIRSTwiki:New users page")
- [User questions](FIRSTwiki:User_questions "FIRSTwiki:User questions")
- **How to edit**
- [Style guide](FIRSTwiki:Style_guide "FIRSTwiki:Style guide")
- [Page formats](FIRSTwiki:Page_formats "FIRSTwiki:Page formats")
- [What to contribute](FIRSTwiki:What_to_contribute "FIRSTwiki:What to contribute")

--------------------------------------------------------------------------------

- [Community decisions](FIRSTwiki:Community_decisions "FIRSTwiki:Community decisions")
- [Village pump](FIRSTwiki:Village_pump "FIRSTwiki:Village pump")
- [Announcements](FIRSTwiki:Announcements "FIRSTwiki:Announcements")
- [Administrator Guide](FIRSTwiki:Guide_for_administrators "FIRSTwiki:Guide for administrators")
- [To Do](FIRSTwiki:To_Do "FIRSTwiki:To Do")
- [Cleanup](FIRSTwiki:Cleanup "FIRSTwiki:Cleanup")
- [Arbitration](FIRSTwiki:Arbitration "FIRSTwiki:Arbitration")

--------------------------------------------------------------------------------

FIRSTwiki is a wiki, meaning anyone can edit any unprotected article and the changes are viewable immediately.

It is very easy to edit a page. Click on the **Edit** tab at the top of the article. You can also discuss a page on its "talk page" -- simply click the **Discuss** tab, and then on the new page, click the **Edit** tab.

Then start typing in the edit box. It is helpful if you write a short description in the **edit summary** box about what you changed. When finished, it is preferred if you first preview your change (click the _Show preview_ button), and once it is satisfactory, commit the change by clicking the _Save page_ button.

To do more advanced edits, you will need to know **Wiki markup**. The following article attempts to describe the most important and most commonly encountered markup, but to get a complete description, see [Wikipedia:How to edit a page](http://www.wikipedia.org/wiki/Wikipedia:How_to_edit_a_page "wikipedia:Wikipedia:How_to_edit_a_page").

## Contents

- 1 Other resources
- 2 General tips

  - 2.1 Page formats

- 3 The wiki markup

  - 3.1 Sections, paragraphs, lists, and lines
  - 3.2 Links, URLs, and images
  - 3.3 Character formatting

- 4 See also

--------------------------------------------------------------------------------

## Other resources

- Tips on [what to contribute](FIRSTwiki:What_to_contribute "FIRSTwiki:What to contribute")
- Style conventions in [FIRSTwiki:Style guide](FIRSTwiki:Style_guide "FIRSTwiki:Style guide")
- General policies in [FIRSTwiki:Policies and guidelines for contributors](FIRSTwiki:Policies_and_guidelines_for_contributors "FIRSTwiki:Policies and guidelines for contributors")
- Page formats to follow in [FIRSTwiki:Page formats](FIRSTwiki:Page_formats "FIRSTwiki:Page formats")

## General tips

- Use a neutral point of view (don't advocate a particular opinion, or use the wiki to advertise)
- Where appropriate, cite your sources
- For longer edits, use a text editor to edit and spell check, then copy and paste back to the wiki and preview before committing the change
- Use the _What links here_ link to make sure all articles linking to your page have in mind the content you provided
- Search the wiki to see if there is similar content in other articles already

[[edit](/index.php?title=FIRSTwiki:How_does_one_edit_a_page&action=edit&sectio
n=3 "Edit section: Page formats")]

### Page formats

You can insert the following wikitext and save to create a default page (make sure you edit it to fill in, ie, the team number). See [FIRSTwiki:Page formats](FIRSTwiki:Page_formats "FIRSTwiki:Page formats") for a complete list and details.

Main team page ([1227](1227 "1227"))

```
 `{{subst:format/team}}`
```

Per-year team page ([1227 in 2004](1227_in_2004 "1227 in 2004"))

```
 `{{subst:format/year}}`
```

Team category ([Category:1227](Category:1227 "Category:1227"))

```
 `{{subst:format/team cat}}`
```

Team table of contents ([Template:toc/1227](Template:Toc/1227 "Template:Toc/1227"))

```
 `{{subst:format/team toc}}`
```

User page

```
 `{{subst:format/user}}`
```

Motor page ([Chiaphua motor](Chiaphua_motor "Chiaphua motor"))

```
 `{{subst:format/motor}}`
```

Game page ([FIRST Frenzy: Raising the Bar](FIRST_Frenzy:_Raising_the_Bar "FIRST Frenzy: Raising the Bar"))

```
 `{{subst:format/game}}`
```

## The wiki markup

To practice editing without fear of harming any particular page, use the [sandbox](FIRSTwiki:Sandbox "FIRSTwiki:Sandbox"). Again, for a comprehensive list of the markup and its effects, see [Wikipedia:How to edit a page](http://www.wikipedia.org/wiki/Wikipedia:How_to_edit_a_page#The_wiki_mark
up "wikipedia:Wikipedia:How_to_edit_a_page").

[[edit](/index.php?title=FIRSTwiki:How_does_one_edit_a_page&action=edit&sectio
n=5 "Edit section: Sections, paragraphs, lists, and lines")]

### Sections, paragraphs, lists, and lines

- To create sections, subsections, and sub-subsections, use the following format:

==New section==<br>
===Subsectiion===<br>
====Sub-subsection====

- A single newline has no affect on the layout, but an empty line starts a new paragraph.
- To add a linebreak, use the HTML markup, <br />
- To create lists, use the following format:

_Lists can be<br>
**Nested quite simply,** Just add an extra_

# and you can create

## numbered lists too

- Use : (a colon) to indent a paragraph
- Bullets (*), numbers (#), and indents (:) can be mixed and matched:

_##_:#**::Something really deep in a list

[[edit](/index.php?title=FIRSTwiki:How_does_one_edit_a_page&action=edit&sectio
n=6 "Edit section: Links, URLs, and images")]

### Links, URLs, and images

- Wrap an article's name in brackets [[like this]] to create a link
- To give the link a new name use a pipe, [[like this|do this]]
- When adding a comment to a talk page, you should sign. Three tildes (~~~) will give your username, and four tildes (~~~~) will give your username and date/time. E.g., [Mrawls](User:Mrawls "User:Mrawls") or [Mrawls](User:Mrawls "User:Mrawls") 15:16, 14 Jun 2004 (EDT)
- To redirect an article to another page, do this #REDIRECT [[Programming]]
- To create an external link, use this syntax: [<http://somepage.com> alternative text]
- To add an image, use this syntax: [[Image:Wiki.png|alt text]]

[[edit](/index.php?title=FIRSTwiki:How_does_one_edit_a_page&action=edit&sectio
n=7 "Edit section: Character formatting")]

### Character formatting

- Add **bold** formatting by using three apostrophes, '''like this'''
- Add _italics_ by using two apostrophes, ''like this''
- For complex mathematical formulae, see [FIRSTwiki:TeX help](FIRSTwiki:TeX_help "FIRSTwiki:TeX help")

## See also

- [FIRSTwiki:User questions](FIRSTwiki:User_questions "FIRSTwiki:User questions")
- [FIRSTwiki:Help](FIRSTwiki:Help "FIRSTwiki:Help")
- [FIRSTwiki:Uneditable Articles](FIRSTwiki:Uneditable_Articles "FIRSTwiki:Uneditable Articles")

Retrieved from "<http://www.firstwiki.netFIRSTwiki:How_does_one_edit_a_page>"

[Category](/index.php?title=Special:Categories&article=FIRSTwiki%3AHow_does_on
e_edit_a_page "Special:Categories"): [Help Pages](Category:Help_Pages "Category:Help Pages")

### Views

- [Project page](FIRSTwiki:How_does_one_edit_a_page)
- [Discussion](FIRSTwiki_talk:How_does_one_edit_a_page)
- [Edit](/index.php?title=FIRSTwiki:How_does_one_edit_a_page&action=edit)
- [History](/index.php?title=FIRSTwiki:How_does_one_edit_a_page&action=history)

### Personal tools

- [Log in / create account](/index.php?title=Special:Userlogin&returnto=FIRSTwiki:How_does_one_edit_a_page)

[](Main_Page "Main Page")

### Navigation

- [Main Page](Main_Page)
- [Community portal](FIRSTwiki:Community_portal)
- [Current events](Current_events)
- [Recent changes](Special:Recentchanges)
- [Random page](Special:Random)
- [Help](Help:Contents)
- [Donations](FIRSTwiki:Site_support)

### Search

### Toolbox

- [What links here](Special:Whatlinkshere/FIRSTwiki:How_does_one_edit_a_page)
- [Related changes](Special:Recentchangeslinked/FIRSTwiki:How_does_one_edit_a_page)
- [Upload file](Special:Upload)
- [Special pages](Special:Specialpages)
- [Printable version](/index.php?title=FIRSTwiki:How_does_one_edit_a_page&printable=yes)
- [Permanent link](/index.php?title=FIRSTwiki:How_does_one_edit_a_page&oldid=64132)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

- This page was last modified 17:11, 12 November 2007.
- This page has been accessed 5,707 times.
- Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html").
- [Privacy policy](FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy")
- [About FIRSTwiki](FIRSTwiki:About "FIRSTwiki:About")
- [Terms and Conditions](FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions")
