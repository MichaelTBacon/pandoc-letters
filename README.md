Pandoc Letters
==============

Generate great looking letters from markdown using Pandoc.

Pandoc Letters lets you easily generate letters from Pandoc Markdown. Letters
are created by defining the letter information in a YAML header and the letter
body text in Pandoc's markdown.

Installation
------------

Download the project and place in a folder of your choice. Make sure the script
file `pandoc-letters` is executable by running `chmod u+x pandoc-letters` if
required.

You can change the default template, signature, output, and source directories
by editing the variables in the top of the `pandoc-letters` script file. I like
to keep my pandoc-letters installation in a `~/doc/correspondence/letters`
directory in my home directory and I work from there, keeping all my letter
related data underneath that folder. That's the reason why the default
directories are what they are at the moment.

Usage
--------------------

`pandoc-letters` is a Bash script that calls Pandoc to create a letter with the
specified options using the specified template. The general format for calling
`pandoc-letters` is:

    pandoc-letters [options] [template] [input-file]

So, a basic usage example would like this:

    ./pandoc-letters formal example.pd

This example will generate a letter using the *formal* template from the input
markdown in `example.pd` located in the default source markdown directory,
`./src`, and places the resulting PDF in the default output directory,
`./dist`.

### Options

*   `-o output-file` - specify the output filename.

    Override the default output filename (FILENAME_DATE.pdf) with the specified
    filename.

*   `-s signature-file` - specify a signature image file.

    The default behaviour is to leave a blank space for signing after printing.
    The default location for signature images is `./resources/signatures`.

*   `-f` - output foldmarks on the letter.

### Templates

The following templates have been implemented:

* **formal** - A simple formal letter style.

    Required YAML metadata fields: `fromname`, `fromaddress (street, city,
    state, zip)`.

    Optional YAML metadata fields: `fromphone`, `fromfax`, `fromemail`,
    `fromurl`, `subject`, `signature`, `addressee (name, title, organization,
    street, city, state, zip)`, `opening`, `closing`, `attachment`, `cc`.

### Letter Markdown

Letters are composed using Pandoc's markdown and a YAML header specifying
letter metadata and template variables.

#### Example Letter

```Markdown
---
fromname: The Stranger
fromaddress:
- street: 123 Broadway
  city: City
  state: State
  zip: 12345
fromphone: +1-123-456-7890
fromfax: +1-123-555-7530
fromemail: thestranger@example.com
subject: An example letter template
addressee:
- name: Jane Smith
  title: Director
  organization: Corporation
  street: 123 Pleasant Lane
  city: City
  state: State
  zip: 12345
attachment: Copyright permission form
cc: executive board
---

Way out west, there was this fella that I wanna tell ya about. A fella by the
name of Jeff Lebowski. At least that was the handle his lovin' parents gave
him, but he never had much use for it himself. This Lebowski, he called himself
'The Dude.'

Now, 'Dude' - that's a name no one would self-apply where I come from. But then
there was a lot about the 'Dude' that didn't make a whole lot of sense to me.
And a lot about where he lived, likewise. But then again, maybe that's why
I found the place so darned interestin'. They call Los Angeles the 'City Of
Angels.' I didn't find it to be that, exactly. But I'll allow there are some
nice folks there. 'Course I can't say I've seen London, and I've never been to
France. And I ain't never seen no queen in her damned undies, as the fella
says. But I'll tell ya what - after seeing Los Angeles, and this a-here story
I'm about to unfold, well, I guess I seen somethin' every bit as stupefyin' as
you'd see in any of those other places. And in English, too. So I can die with
a smile on my face, without feelin' like the good Lord gypped me.

Now this a-here story I'm about to unfold took place back in the early '90s
- just about the time of our conflict with Sad'm and the I-raqis. I only
mention it because sometimes there's a man - I won't say a hero, 'cause, what's
a hero? But sometimes, there's a man - and I'm talkin' about the 'Dude' here.
Sometimes, there's a man, well, he's the man for his time and place. He fits
right in there. And that's the 'Dude' in Los Angeles. And even if he's a lazy
man - and the 'Dude' was most certainly that, quite possibly the laziest in Los
Angeles County, which would place him high in the runnin' for laziest
worldwide. But sometimes there's a man, sometimes, there's a man.

Wow, I lost my train of thought here. But, aw, hell. I've done introduced him
enough.

```

#### YAML Metadata

The following provides a brief explanation of each of the YAML metadata fields and the templates that support the fields.

* `fromname` - the name of the sender.

    Templates: *formal*.

* `fromaddress` - the address of the sender.

    The `fromaddress` field has the following subfields:

    * `street` - the street name.
    * `city` - the city name.
    * `state` - the state name or abbreviation.
    * `zip` - the zip code.

    Templates: *formal*.

* `fromphone` - the phone number of the sender.

    Templates: *formal*.

* `fromfax` - the fax number of the sender.

    Templates: *formal*.

* `fromemail` - the email address of the sender.

    Templates: *formal*.

* `fromurl` - the URL of the sender.

    Templates: *formal*.

* `subject` - the subject of the letter.

    Templates: *formal*.

* `signature` - the signature name. Default: `fromname`.

    Templates: *formal*.

* `adressee` - the recipient of the letter.

    The `addressee` field has the following subfields:

    * `name` - the name of the recipient.
    * `title` - the title of the recipient.
    * `organization` - the organization of the recipient.
    * `street` - the street name of the recipient.
    * `city` - the city name of the recipient.
    * `state` - the state name or abbreviation of the recipient.
    * `zip` - the zip code of the recipient.

    Templates: *formal*.

* `opening` - the opening of the letter. Default: *Dear Sir or Madam,*.

    Templates: *formal*.

* `closing` - the closing of the letter. Default: *Sincerely,*.

    Templates: *formal*.

* `attachment` - the title of an attachment to the letter. Note: `pandoc-letters` does not actually attach the attachment to the output.

    Templates: *formal*.

* `cc` - a carbon copy recipient.

    Templates: *formal*.


