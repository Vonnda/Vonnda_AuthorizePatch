# Vonnda_AuthorizePatch
Patch for Authorize.net API change to supported characters on 1/22/2019

## Installation
To install you can either use modman or move the files into the respective locations. You can install modman from here https://github.com/colinmollenhour/modman

    modman clone git@github.com:Vonnda/Vonnda_AuthorizePatch.git

## Description of Auth.net API change
To ensure that we are providing our merchants with the highest level of security, we are no longer allowing the following characters to be included in field values. These characters are:

| Invalid Char                    | Replacement            |
| ------------------------------- | ---------------------- |
| ASCII < 32 (control characters) | `‘ ’` (one space)      |
| ‘<’                             | ‘ ’ (one space)        |
| ‘>’                             | ‘ ’ (one space)        |
| %3C (URL encode of ‘<’)         | `‘   ’` (three spaces) |
| %3E (URL encode of ‘>’)         | `‘   ’` (three spaces) |
| &lt;  (HTML encode of ‘<’)      | `‘    ’` (four spaces) |
| &gt; (HTML encode of ‘>’)       | `‘    ’` (four spaces) |

For those passing Unicode characters, the following is the Unicode range we support. Any Unicode characters received outside this range will be replaced with spaces:

* 0x0020 to 0x02AF
* 0x0370 to 0x20CF
* 0x2150 to 0x218F
* 0x2200 to 0x22FF
* 0x2460 to 0x24FF
* 0x2C00 to 0x2C5F
* 0x2C60 to 0x2C7F
* 0x2C80 to 0x2CFF
* 0x2D00 to 0x2D2F
* 0x2E80 to 0xD7FF
* 0xF900 to 0xFFEF

## References to change
https://support.authorize.net/s/article/Changes-to-Supported-Characters
https://community.developer.authorize.net/t5/News-and-Announcements/Changes-to-Supported-Characters-Jan-22-2019/td-p/65435
