# Office 365 GeoLogonalyzer.

### Thanks goes out to [fireeye](https://github.com/fireeye/GeoLogonalyzer). I modified this to work for O365 logs and to provide me with City And State.

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
    
### MaxMind Database downloads
Create an account and download the GZIP for the following databases:
    1. [GeoLit2 ASN](https://www.maxmind.com/en/accounts/250539/geoip/downloads)
    2. [GeoLite2 City](https://www.maxmind.com/en/accounts/250539/geoip/downloads)
Extract the .mmdb to the same folder as the script.

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

-----
# Licenses
### GeoLogonalyzer License: 
    This product is licensed under the Apache License, Version 2.0 and is
    Copyright <C> 2018 FireEye, Inc. You may obtain a copy of the License
    at: http://www.apache.org/licenses/LICENSE-2.0. Unless required by
    applicable law or agreed to in writing, software distributed under the
    License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
    CONDITIONS OF ANY KIND, either express or implied. See the License for
    the specific language governing permissions and limitations under the
    License.

### MaxMind Attribution and Credit

    This product includes GeoLite2 data created by MaxMind, available from
    http://www.maxmind.com provided under the Creative Commons Attribution-
    ShareAlike 4.0 International License. Copyright (C) 2012-2018 Maxmind, Inc.
    Copyright (C) 2012-2018 Maxmind, Inc.

### client9 Attribution and Credit

    This product retrieves and operates on data including datacenter
    categorizations retrieved from https://github.com/client9/ipcat/ which
    are Copyright <C> 2018 Client9. This data comes with ABSOLUTELY NO
    WARRANTY; for details go to:
            https://raw.githubusercontent.com/client9/ipcat/master/LICENSE
    The data is free software, and you are welcome to redistribute it under
    certain conditions. See LICENSE for details.

# Limitations
1. All GeoIP lookups are dependent on the accuracy of MaxMind database values
2. All DCH lookups are dependent on the accuracy of open source data
3. VPN or network tunneling services may skew results

# Credits
GeoLogonalyzer was created by David Pany. The project was inspired by research performed by FireEye's data science team including Christopher Schmitt, Seth Summersett, Jeff Johns, Alexander Mulfinger, and more whose work supports live remote access processing in FireEye Helix - https://www.fireeye.com/solutions/helix.html. The "Logonalyzer" name was originally created by @0xF2EDCA5A.
