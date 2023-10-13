# Resource Usage

This script is designed to collect resource usage data for a command and output it in a CSV format on stderr.

## Requirements

Depending on your hardware you need different dependencies

### NVIDIA

- nvml

## Install

### Windows

Install LibreHardwareMonitor to access the CPU registry
```
Create:

`sc create rapl type= kernel binPath= "<path_to_LibreHardwareMonitor.sys>"`

Start:

`sc start rapl`

Stop:

`sc stop rapl`

Delete:

`sc delete rapl`

cargo build;
```


### Linux

```
sudo chgrp -R msr /dev/cpu/*/msr;
sudo chmod g+r /dev/cpu/*/msr;
cargo build;
sudo setcap cap_sys_rawio=ep target/debug/energy_bridge; # Any non-root program accessing the msr also needs the rawio capability
```

## Usage

To run the script, use the following command:

```
Usage: energi_bridge[.exe] [OPTIONS] [COMMAND]...

Arguments:
  [COMMAND]...

Options:
  -o, --output <OUTPUT>

  -s, --separator <SEPARATOR>
          [default: ,]
  -c, --command-output <COMMAND_OUTPUT>

  -i, --interval <INTERVAL>
          Duration of the interval between two measurements in micoseconds [default: 100]
  -g, --gpu

  -h, --help
          Print help
  -V, --version
          Print versio
```

## Output


```csv
Time,Thread0 Core Effective Frequency,Thread1 Core Effective Frequency,Thread2 Core Effective Frequency,Thread3 Core Effective Frequency,Thread4 Core Effective Frequency,Thread5 Core Effective Frequency,Thread6 Core Effective Frequency,Thread7 Core Effective Frequency,Thread8 Core Effective Frequency,Thread9 Core Effective Frequency,Thread10 Core Effective Frequency,Thread11 Core Effective Frequency,Thread12 Core Effective Frequency,Thread13 Core Effective Frequency,Thread14 Core Effective Frequency,Thread15 Core Effective Frequency,Thread16 Core Effective Frequency,Thread17 Core Effective Frequency,Thread18 Core Effective Frequency,Thread19 Core Effective Frequency,Thread20 Core Effective Frequency,Thread21 Core Effective Frequency,Thread22 Core Effective Frequency,Thread23 Core Effective Frequency,Thread0 P-State,Thread1 P-State,Thread2 P-State,Thread3 P-State,Thread4 P-State,Thread5 P-State,Thread6 P-State,Thread7 P-State,Thread8 P-State,Thread9 P-State,Thread10 P-State,Thread11 P-State,Thread12 P-State,Thread13 P-State,Thread14 P-State,Thread15 P-State,Thread16 P-State,Thread17 P-State,Thread18 P-State,Thread19 P-State,Thread20 P-State,Thread21 P-State,Thread22 P-State,Thread23 P-State,Socket0 Package Power,Core0 Power,Core1 Power,Core2 Power,Core3 Power,Core4 Power,Core5 Power,Core6 Power,Core7 Power,Core8 Power,Core9 Power,Core10 Power,Core11 Power,Socket0 Temperature,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Thread24 Core Usage,Process CPU Usage,Memory Total,Memory Free,Memory Usage,Process Memory Usage,GPU Usage,GPU Power,GPU Temperature,GPU Memory Total,GPU Memory Usage
2023-06-02T13:20:49.462403364,5375.03,5375.03,5375.04,5375.03,5375.02,5375.02,5234.7,5234.7,5234.71,5234.71,5234.71,5234.71,5375.05,5375.03,5375.04,5375.05,5375.02,5375.03,5234.7,5234.71,5234.71,5234.7,5234.71,5234.7,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,137.737,14.476,14.5966,14.9719,15.1489,14.9902,15.6113,13.5864,13.8168,13.8016,14.1861,13.7817,13.7436,72.5,0.263945,0.238525,0.222255,0.14201,0.23434,0.291398,0.509058,0.26057,0.270727,0.252942,0.48244,0.274229,0.283855,0.260922,0.244906,0.256021,0.254829,0.244498,0.264985,0.242692,0.218433,0.211244,0.254231,0.206116,582408,66497908736,57947361280,12,32496,0,19,39,25757220864,369819648
2023-06-02T13:20:49.655847839,5382.3,5382.31,5382.3,5382.3,5382.32,5382.32,5239.1,5239.1,5239.1,5239.1,5239.1,5239.1,5382.3,5382.33,5382.31,5382.32,5382.31,5382.32,5239.1,5239.1,5239.1,5239.1,5239.1,5239.1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,137.14,14.5432,14.6225,14.9979,15.1962,15.0421,15.6754,13.7924,13.8641,13.8626,14.1861,13.8412,13.797,72.5,5382.88,5382.85,5382.86,5382.86,5382.84,5382.85,5234.79,5234.81,5234.79,5234.81,5234.81,5234.81,5382.88,5382.83,5382.84,5382.84,5382.85,5382.83,5234.81,5234.79,5234.82,5234.8,5234.82,5234.8,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,124.074,13.7175,13.6809,14.2267,14.2435,14.1581,14.5941,12.9339,12.9431,12.9736,13.2373,12.8257,12.8318,72.5,0.264158,0.238735,0.222466,0.14222,0.23455,0.291608,0.509267,0.260781,0.270937,0.253152,0.48265,0.27445,0.284077,0.261143,0.245116,0.256243,0.25505,0.24472,0.265196,0.242902,0.218655,0.211454,0.254453,0.206326,582408,66497908736,57934987264,12,32496,0,17,39,25757220864,369819648
2023-06-02T13:20:49.845747408,5375.84,5375.84,5375.84,5375.85,5375.84,5375.83,5234.55,5234.57,5234.56,5234.56,5234.56,5234.56,5375.95,5375.97,5375.85,5375.83,5375.83,5375.95,5234.56,5234.55,5234.56,5234.56,5234.55,5234.57,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,137.167,14.5416,14.6439,15.0116,15.1718,15.0375,15.509,13.7802,13.858,13.8794,14.2456,13.9755,13.7955,72.375,5369.24,5369.23,5369.21,5369.23,5369.21,5369.22,5233.24,5233.25,5233.24,5233.26,5233.24,5233.24,5369.11,5369.08,5369.2,5369.25,5369.22,5369.09,5233.23,5233.26,5233.24,5233.24,5233.24,5233.25,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,123.563,13.6535,13.7556,14.1063,14.2785,14.1962,14.7481,12.7144,13.0483,13.1519,13.2693,13.2114,12.9248,72.375,5379.77,5379.77,5379.78,5379.77,5379.79,5379.78,5239.52,5239.51,5239.52,5239.52,5239.5,5239.52,5379.77,5379.76,5379.78,5379.76,5379.78,5379.78,5239.53,5239.51,5239.53,5239.52,5239.52,5239.49,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,123.645,13.5178,13.7466,14.0381,13.9847,13.9938,14.6454,13.031,12.9486,13.1592,13.2767,13.1516,12.9578,72.375,0.26437,0.238956,0.222676,0.142431,0.23476,0.291818,0.509477,0.261002,0.271147,0.253362,0.48286,0.274661,0.284287,0.261353,0.245327,0.256453,0.25526,0.24493,0.265406,0.243112,0.218865,0.211676,0.254663,0.206547,582408,66497908736,57933729792,12,32496,0,20,39,25757220864,369819648
2023-06-02T13:20:50.046040974,5384.29,5384.3,5384.3,5384.3,5384.3,5384.3,5222.46,5222.44,5222.45,5222.45,5222.45,5222.44,5384.3,5384.32,5384.3,5384.3,5384.3,5384.32,5222.45,5222.45,5222.48,5222.45,5222.46,5222.46,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,136.645,14.4981,14.6231,14.9935,15.0713,15.0362,15.5347,13.7404,13.8258,13.8136,14.1444,13.8517,13.7267,72.375,5378.06,5378.07,5378.07,5378.07,5378.07,5378.07,5227.48,5227.49,5227.48,5227.5,5227.49,5227.51,5378.04,5378.04,5378.07,5378.07,5378.04,5378.03,5227.49,5227.48,5227.45,5227.49,5227.48,5227.5,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,124.472,13.7389,13.5039,13.8869,14.1524,14.1234,14.4836,12.7042,13.0216,13.0537,13.0079,12.9636,13.0369,72.375,0.264591,0.239178,0.222897,0.142652,0.234982,0.292039,0.509698,0.261223,0.271368,0.253584,0.483081,0.274882,0.284497,0.261574,0.245548,0.256674,0.255481,0.245151,0.265627,0.243334,0.219086,0.211897,0.254884,0.206769,582408,66497908736,57930113024,12,32496,0,20,39,25757220864,369819648
2023-06-02T13:20:50.246348806,5380.08,5380.07,5380.09,5380.07,5380.06,5380.09,5238.23,5238.24,5238.24,5238.24,5238.24,5238.24,5380.1,5380.09,5380.07,5380.07,5380.07,5380.06,5238.23,5238.24,5238.24,5238.23,5238.24,5238.24,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,137.369,14.6926,14.6362,15.0512,15.1337,14.9032,15.5625,13.5786,14.1356,13.8594,14.247,13.9846,13.8121,72.25,5386.85,5386.86,5386.85,5386.87,5386.87,5386.84,5233.45,5233.45,5233.45,5233.45,5233.45,5233.44,5386.84,5386.85,5386.86,5386.87,5386.87,5386.87,5233.45,5233.44,5233.44,5233.45,5233.45,5233.45,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,125.368,13.7878,13.913,14.5264,14.3524,14.3753,14.5752,12.7365,13.3743,12.9944,13.0356,13.0432,12.8006,72.25,0.264812,0.239399,0.223119,0.142874,0.235203,0.292261,0.509918,0.261444,0.271589,0.253805,0.483301,0.275103,0.284718,0.261795,0.245769,0.256884,0.255703,0.245372,0.265848,0.243555,0.219307,0.212118,0.255105,0.20699,582408,66497908736,57929080832,12,32496,0,19,39,25757220864,369819648
2023-06-02T13:20:50.446395643,5385.76,5385.74,5385.76,5385.74,5385.74,5385.77,5234.64,5234.65,5234.63,5234.65,5234.64,5234.63,5385.74,5385.76,5385.75,5385.75,5385.73,5385.74,5234.63,5234.64,5234.63,5234.65,5234.64,5234.63,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,149.646,16.111,15.9723,16.3884,16.579,16.425,16.8793,15.024,15.1246,15.0819,15.6643,15.1002,15.0423,72.25,5366.77,5366.81,5366.77,5366.81,5366.82,5366.75,5232.89,5232.87,5232.9,5232.88,5232.9,5232.9,5366.8,5366.79,5366.78,5366.8,5366.81,5366.8,5232.89,5232.89,5232.89,5232.88,5232.9,5232.89,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,110.803,13.8169,13.6229,13.9452,14.3301,14.0521,14.3866,12.8669,13.2182,12.9677,13.1235,13.1937,13.1174,72.25,0.265034,0.23962,0.22334,0.143095,0.235424,0.292482,0.510139,0.261665,0.271811,0.254026,0.483522,0.275324,0.284939,0.262017,0.24599,0.257106,0.255924,0.245594,0.266069,0.243776,0.219529,0.21234,0.255327,0.207211,582408,66497908736,57928040448,12,32496,0,20,39,25757220864,369819648
```

## TODO

- Extends Mac supports by looking at https://github.com/dehydratedpotato/socpowerbud/
