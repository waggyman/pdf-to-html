[![Build Status](https://travis-ci.org/mgufrone/pdf-to-html.svg?branch=master)](https://travis-ci.org/mgufrone/pdf-to-html)



# PDF to HTML PHP Class

This class brought to you so you can use php and poppler-utils convert your pdf files to html file

## Important Notes

Please see how to use below, since it's really upgraded and things in this package has already changed.

## Installation

When you are in your active directory apps, you can just run this command to add this package on your app

```
	composer require gufy/pdftohtml-php:~2
```

Or add this package to your `composer.json`

```json
{
	"gufy/pdftohtml-php":"~2"
}
```

## Requirements
1. Poppler-Utils (if you are using Ubuntu Distro, just install it from apt )
	`sudo apt-get install poppler-utils`
2. PHP Configuration with shell access enabled

## Usage

Here is the sample.

```php
<?php
// if you are using composer, just use this
include 'vendor/autoload.php';

// initiate
$pdf = new Gufy\PdfToHtml\Pdf('file.pdf');

// convert to html and return it as [Dom Object](https://github.com/paquettg/php-html-parser)
$html = $pdf->html();

// check if your pdf has more than one pages
$total_pages = $pdf->getTotalPages();

// Your pdf happen to have more than one pages and you want to go another page? Got it. use this command to change the current page to page 3
$html->goToPage(3);

// and then you can do as you please with that dom, you can find any element you want
$paragraphs = $html->find('body > p');

// change pdftohtml bin location
\Gufy\PdfToHtml\Config::set('pdftohtml.bin', '/usr/local/bin/pdftohtml');

// change pdfinfo bin location
\Gufy\PdfToHtml\Config::set('pdfinfo.bin', '/usr/local/bin/pdfinfo');
?>
```

## Usage note for Windows Users
For those who need this package in windows, there is a way. First download poppler-utils for windows here <http://blog.alivate.com.au/poppler-windows/>. And download the latest binary.

After download it, extract it. There will be a directory called `bin`. We will need this one. Then change your code like this


```php
<?php
// if you are using composer, just use this
include 'vendor/autoload.php';
use Gufy\PdfToHtml\Config;
// change pdftohtml bin location
Config::set('pdftohtml.bin', '/path/to/poppler/bin/pdftohtml.exe');

// change pdfinfo bin location
Config::set('pdfinfo.bin', '/path/to/poppler/bin/pdfinfo.exe');
// initiate
$pdf = new Gufy\PdfToHtml\Pdf('file.pdf');

// convert to html and return it as [Dom Object](https://github.com/paquettg/php-html-parser)
$html = $pdf->html();

// check if your pdf has more than one pages
$total_pages = $pdf->getTotalPages();

// Your pdf happen to have more than one pages and you want to go another page? Got it. use this command to change the current page to page 3
$html->goToPage(3);

// and then you can do as you please with that dom, you can find any element you want
$paragraphs = $html->find('body > p');

?>
```

## Feedback & Contribute

Send me an issue for improvement or any buggy thing. I love to help and solve another people problems. Thanks :+1:
