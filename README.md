# Project3

There are 2 different datasets for this project. The first dataset, which is within the foler, "Results", was performed on the RPI provided Lenovo Thinkpad laptop. It was performed using the "Ubuntu 20.04 on Windows" CLI, downloaded from the Windows Store. The second dataset, "VM_Results", was performed using an Ubuntu 20.04 LTS virtual machine running on VirtualBox on the same Lenovo as the previous dataset. This information is important because the latency for between both datasets are radically different, so it was necessary to give the disclaimer. 


# Part 1: Data Access Size

The experiment begins with testing the different data sizes to see how they affect throughput and latency. Seeing as this part of the project deals only with testing different batch sizes, we kept the ```iodepth``` variable fixed to the value of 1. On the other hand, we set the ```numjobs``` variable to the value of 8 so that we could  The command we ran was , ```fio --filename/dev/sdb --rw-read --direct=1 --bs=4K ==ioengine=sync --runtime=20 --numjobs=8 --time_based --group_reporting --name=speed_job --iodepth=1 --size=1048576```


![](https://github.com/danielle-den/Project3/blob/main/figures/4K%20read%20iodepth%201.png)


