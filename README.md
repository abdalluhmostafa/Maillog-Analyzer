Postfix log analyzer maillog
Introduction
When the mail server processes the letter, it writes several lines to the log file. With large mail traffic, lines related to different letters are mixed, sometimes records related to one letter are separated by several tens of lines from each other. This greatly interferes with reading logs. To solve this problem, in ancient times I wrote a pearl script with the original name maillog. Over time, functionality was added to it, bugs were fixed. And now, when there are questions with the mail, the first thing we do is run this script.

Opportunities.
The script scans the log files, groups the lines by letters. Records are highlighted in color depending on delivery success, addresses are highlighted.

It is possible to filter messages by sender and / or sender, the -f and -t keys, respectively.

Using the -d switch, you can specify the date or date range for which to display letters. Dates can be set in different ways, for example:

12.1.2010-15.1.2010 - show letters from the 12th to the 15th inclusively. 01/10/2010 - - letters that have passed since the 10th and later. -12.01 - the opposite of the previous option, the 12th and earlier. If the year or month is omitted, then the current ones are substituted. - - in general, all that happened on January 1, 2010 is for January 1, 2010. By default, letters for today are displayed.

If you want to see only letters with errors, i.e. which were not delivered, you can use the -e option.

All of these keys can be used in any combination.

There is support for log files compressed after rotation.

Customization.
There are not many settings :) At the beginning of the script there is a line "my $ filePattern = '/ var / log / mail / mail * .log';" it sets the name template for the mail server logs.

Limitations
Only date and month are written in the logs, so it is impossible to filter letters by year. You can always omit the year in the -d option. If anyone has thoughts, write to me.

I have a month in the log written in English Jan, Feb, etc., if someone has them in Russian, add Russian elements to the% MONTHS hash.

The script only works with postfix logs. I don’t remember now the logs of other servers are very different, it is possible to really add support for other programs.

Use (help).
 Usage: maillog [-d DATE] [-f FROM] [-t TO] [-e] [-h] [-V]

 Shows entries in the mail log for letters coming from the FROM address to
 address for the period specified in the DATE option.

   -f FROM postal address of the sender (or part thereof).

   -t TO   recipient's mailing address (or part thereof).

   -d DATE report for the specified period if the option is omitted
           records for the current day only are displayed.

     DD/MM/YY-DD/MM/YY   Full format

   -e      only show undelivered messages.

   -h      show the help page.

   -V      show program version and license.
