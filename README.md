# Ruckus SmartZone API

Repository for basic python scripts to pull and print data from Ruckus SmartZone API.

# Note

I am new to both python and git and scripts are training exercises. I have not written code for an extended period.
Program is tested against a SZ100 cluster of 2 running 3.6.2. These scripts work correctly with vSZ-E but not with vSZ-H. Read-only account is reccomended. 

### Each script will need the following variables which will need modifying for your own configuration:

* `baseurl`
    * "https://general.direction.com:8443/wsg/api/public/v6_1/" # replace "general.direction.com" with the host name or IP of a member of the cluster
* `szusername`
    * String
* `szpassword`
    * String

Use API documentation below for reference:

[Ruckus documentation for version 3.6.2](http://docs.ruckuswireless.com/smartzone/3.6.2/sz100-public-api-reference-guide-3-6-2.html)

## login_getzone.py

Returns and prints all the configured zones on the cluster. The script will output a list of lists called `cleaned_zones`.

Format of the lists are:

`[name_of_zone,zone_id]`

## login_getwlans.py

Builds on `login_getzone.py` to produce a list of lists called  `cleaned_all_zone_wlan`  from  `cleaned_zones`  that includes the WLAN names and ids. Please note this is the WLAN name NOT the SSID.

Format of the lists are:

`[name_of_zone,zone_id,name_of_WLAN,WLAN_id]`

## login_getwlan_details.py

Returns and prints the JSON from individual WLAN. If  `wlan_template_id`  or `zone_template_id`  are blank program will ask for the names of the WLAN and the zone to be inputted. The script attempts to account for spelling mistakes in the WLAN name before quitting if WLAN is not found in the zone.

It will save the WLAN's details in a variable called `wlan_template`.
