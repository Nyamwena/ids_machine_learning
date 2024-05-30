## Usage

It has two main components which should be executed in separate console windows.

### 1) Monitor

It reads packets either from a PCAP file or a network interface. 


 On linux systems you may need to install the `libpcap` library and `tcpdump` software.
 
  On Windows, you need to install [Npcap](https://npcap.com/#download) and [WinDump](https://github.com/hsluoyz/WinDump/releases) to run the monitor.

Read packets from a PCAP file:

```sh
python monitor.py -f /home/user/ids_using_ml/example_pcap/traffic_5f_ni.pcap
```

```sh
sudo python monitor.py -i eno1
```

```sh
Options:
  -w, --warning-threshold FLOAT RANGE
                            Warning threshold from 0 to 100 w.r.t. the
                            confidence score.  [default: 40.0; 0<=x<=100]
  -a, --alert-threshold FLOAT RANGE
                            Alert threshold from 0 to 100 w.r.t. the confidence
                            score.  [default: 50.0; 0<=x<=100]
  -r, --refresh-millisecond INTEGER
                            Refresh results after every r milliseconds. [default: 250]
  -s, --show-flows INTEGER  Maximum number of flows to display.  [default: 100]

```

## Example

1) Run the **display** to show 50 recently updated flows and update the results after every 500 milliseconds.

```sh
python display.py -s 50 -r 500 -w 40 -a 50
#for windows
python display.py -u 127.0.0.1:9400 -s 50 -r 500 -w 40 -a 50
 
```

```

![monitor's output in the terminal](./doc_images/term_display.svg)

2) Run the **monitor** to read every packet from the given PCAP file with a delay of 1000 milliseconds and use a trained model to get predictions:

```sh
python monitor.py -f example_pcap/traffic_5f_ni.pcap -c trained_cicids17 -d 1000
```


