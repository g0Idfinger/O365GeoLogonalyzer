# Office 365 Geo Login and Anomoly Parser.

# Thanks goes out to [fireeye](https://github.com/fireeye/GeoLogonalyzer). I modified this to work for O365 logs and to provide me with City And State.

Pull CSV from O365 successful Logins. 


# Preparation

###  Python
If you need to use the python source code (such as for modifiying configurations, adding custom
log parsing, or running on *nix/OSX), you will need to install the following dependencies which 
you may not already have:

    netaddr
    python-geoip
    win_inet_pton
    geopy
    geoip2

A pip requirements.txt is provided for your convenience.

    pip install -r requirements.txt

# Execution Syntax
The following command will parse the input.csv shown above and save results to output.csv:

    GeoLogonalyzer --csv input.csv --output output.csv
    ------
# Output
The output.csv file will include the following column headers:

| Column Header | Description |
|-------------|-----------|
| User | Username of logons compared |
| Anomalies | Flags for anomalies detailed in "Automatic Anomaly Detection" section below |
| 1st Time | Time of 1st compared logon |
| 1st IP | IP Address of 1st compared logon |
| 1st State| State of 1st compared logon |
| 1st Country | Country associated with IP address of 1st compared logon |
| 1st City | City associated with IP address of 1st compared logon |
| 1st Coords | Lat/Long coordinates associated with IP address of 1st compared logon |
| 1st ASN # | ASN number associated with IP address of 1st compared logon |
| 1st ASN Name | ASN name associated with IP address of 1st compared logon |
| 1st VPN Client | VPN client name associated with 1st compared logon |
| 1st Hostname | Hostname associated with 1st compared logon |
| 1st Streak | Count of logons by user from 1st compared source IP address before change |
| 2nd Time | Time of 2nd compared logon |
| 2nd IP | IP Address of 2nd compared logon |
| 2nd State | State of 2nd compared logon |
| 2nd Country | Country associated with IP address of 2nd compared logon |
| 2nd City | City associated with IP address of 2nd compared logon |
| 2nd Coords | Lat/Long coordinates associated with IP address of 2nd compared logon |
| 2nd ASN # | ASN number associated with IP address of 2nd compared logon |
| 2nd ASN Name | ASN name associated with IP address of 2nd compared logon |
| 2nd VPN Client | VPN client name associated with 2nd compared logon |
| 2nd Hostname | Hostname associated with 2nd compared logon |
| Miles Diff | Difference in miles between two associated coordinates of two compared IP addresses |
| Seconds Diff | Difference in time between two compared authentications |
| Miles/Hour | Speed required to physically move from 1st logon location to 2nd logon location by time difference between compared logons. Miles Diff / Seconds Diff |
