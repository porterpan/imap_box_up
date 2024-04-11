# imap

[![Documentation Status](https://readthedocs.org/projects/imap/badge/?version=latest)](https://imap.readthedocs.io/en/latest/?badge=latest)

**[imap](https://imap.readthedocs.io/en/latest/)** is a tool for visualize and convert format of the hd-map. This project was inspired by Apollo. 

I called the modified with **imap_box_up** , Just to differentiate it from imap_box

imap_box_up code: https://github.com/porterpan/imap_box_up

**Note:**

Modified on project [https://github.com/daohu527/imap](https://github.com/daohu527/imap)

> I found that imap_box had the problem of inaccurate junction drawing, which could not meet the needs of my project. Therefore, I modified imap_box based on it to adapt to appollo hdmap code. 



![example]([eg1.png](https://private-user-images.githubusercontent.com/30954452/321745045-d23d05d2-66a4-4690-bf17-073c7fd4bbe3.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTI4NjA3NjQsIm5iZiI6MTcxMjg2MDQ2NCwicGF0aCI6Ii8zMDk1NDQ1Mi8zMjE3NDUwNDUtZDIzZDA1ZDItNjZhNC00NjkwLWJmMTctMDczYzdmZDRiYmUzLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDA0MTElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwNDExVDE4MzQyNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTE4NDYyY2ZkZjQxMjQ2YTZiZmVmMWI2YTg3ZTA3NGZlMzNjNTY3ZTIxZDFhZDY1NjdlZWFiYWM1YTk2YjI0MTAmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.GhurdLnE04-8-OwlWQF2VWgymB4e-EX-hAONUX1pQaM))

**Supported features**:
1. Visualize the hd-map, supported formats: Apollo, OpenDrive.
2. Find lane by id
3. Convert format: Opendrive to Apollo format.

| os      | support                 | remark |
|---------|-------------------------|--------|
| ubuntu  | :heavy_check_mark:      |        |
| mac     | :heavy_check_mark:      |        |
| windows | :heavy_check_mark:      |        |

## Related work
- [odrviewer.io](https://odrviewer.io/) is an excellent interactive online OpenDRIVE viewer.
- [esmini](https://github.com/esmini/esmini) is a basic OpenSCENARIO player.
- [apollo_map](https://github.com/Flycars/apollo_map) convert carla map to apollo

## Quick start

#### Install
You can install imap by following cmd.
```shell
pip3 install imap_box_up
```

## Example
#### 1. Visualization
After the installation is complete, you can view the map with the following command.
```shell
imap -m data/borregas_ave.txt
// or
imap -m data/town.xodr
```
Currently supported formats:
* Apollo map
* OpenDrive map

#### 2. Find lane by id
You can use below command to find lane by id, Found lane is shown in **Red**.
```shell
imap -m data/borregas_ave.txt -l lane_35
```

#### 3. Format conversion
Now you can convert OpenDrive map to Apollo map by following command.
```shell
imap -f -i data/town.xodr -o data/apollo_map.txt
```
you should better reference follow command to convert apollo map to OpenDrive map.

 1.show appollo map by id:

 ```shell
 imap -m data/borregas_ave.txt -l lane_35
 ```

2.Format conversion with UTM map(opendrive->appollo): 

```shell
imap -f -i data/town.xodr -o data/apollo_map.txt
```
3.Format conversion with inertial map(opendrive->appollo.inertial map):

```shell
imap -f -r -i data/town.xodr -o data/apollo_map.txt
```



The following is the display of the hd-map in `data\borregas_ave.txt`.You can click on the lane you want to display more detail info, which will display the current lane's id, as well as the predecessor and successor lane's id in the upper left corner.

![map_show](docs/_static/map_show.jpg)


## Questions
1. After running the command `imap -m data/your_map_file`, nothing display and no errors!!!

A: Check the permissions of the map file, if the current user does not have permissions, modify the permissions with the following commands.
```shell
sudo chmod 777 data/your_map_file
```
2. Map data permission checking has no problem, still nothing display and no errors!
A: It's better to install imap_box by running "sudo pip3 install imap_box", then run "imap -m xxx.txt".
