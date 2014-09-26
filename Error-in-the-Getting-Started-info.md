There is an error in the 'Easiest' way to get started info on the Font-Awesome website:

<link href="//maxcdn.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.min.css" rel="stylesheet">

This link appears on this page at the top: http://fontawesome.io/get-started/

The link is not properly closed and will cause an error on some sites.  It should be:

<link href="//maxcdn.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.min.css" rel="stylesheet" />

Note the '/>' at the end.  
  