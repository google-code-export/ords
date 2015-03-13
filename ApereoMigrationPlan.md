# Introduction #

We are thinking of migrating Oxford Database-as-a-Service development work to Apereo, making it an official Apereo incubator project, and finally making it properly open source, with a licence and everything!

But how much work will this require? Please add the activities we will need to undertake below, with a rough estimation of how long each will take in mythical man-days.


# Details #

  * Create debranded version of DaaS (with all Oxford-specific content in a separate file that can easily be added). This will include images and text
  * Separate registration/log-in process so that other institutions can easily substitute their own versions without forking the code
  * Put the contact email address (ords@it.ox.ac.uk) into a config file for easy changing.
  * Ensure that there's nothing hard-coded into ORDS that might result in any security issues