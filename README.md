# Project3

There are 2 different datasets for this project. The first dataset, which is within the foler, "Results", was performed on the RPI provided Lenovo Thinkpad laptop. It was performed using the "Ubuntu 20.04 on Windows" CLI, downloaded from the Windows Store. The second dataset, "VM_Results", was performed using an Ubuntu 20.04 LTS virtual machine running on VirtualBox on the same Lenovo as the previous dataset. This information is important because the latency for between both datasets are radically different, so it was necessary to give the disclaimer. 


# Part 1: Data Access Size

The experiment begins with testing the different data sizes to see how they affect throughput and latency. Seeing as this part of the project deals only with testing different batch sizes, we kept the ```iodepth``` variable fixed to the value of 1. Moreover, the ```numjobs``` variable was set to the value of 8, so the latency and bandwitdth are much higher than usual. This was intentionally done simply to show that the queueing theory is valid for high number of jobs. The command we ran was , ```fio --filename/dev/sdb --rw-read --direct=1 --bs=4K ==ioengine=sync --runtime=20 --numjobs=8 --time_based --group_reporting --name=speed_job --iodepth=1 --size=1048576```


As we increased the batch size from 4K to 128K, the throughput/bandwidth increased since the SSD is being utilized more and more. At the same time, the average latency was increasing, as predicted by the queuing theory. 

![](https://github.com/danielle-den/Project3/assets/143743140/d91db6ba-af47-4d66-ac06-dbddbf388149)    ![](https://github.com/danielle-den/Project3/blob/main/figures/1%20iodepth%20read%20Latency.png)

## Write
Those were the results of the ```--rw-read``` operation, so we decided to see how the SSD would fare when it came to the write operation. The expectation was that the queueing theory to still be followed but with different magnitudes in throughput and latency. As the graphs below show, our expectations were correct and the trend of the previous graphs were realized here as well ; as the batch sizes increased, the latency and throughput increased.

On the other hand, the IOPS for both the purely read and purely write operations decreased. 





