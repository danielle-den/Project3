# Project3

There are 2 different datasets for this project. The first dataset, which is within the foler, "Results", was performed on the RPI provided Lenovo Thinkpad laptop. It was performed using the "Ubuntu 20.04 on Windows" CLI, downloaded from the Windows Store. The second dataset, "VM_Results", was performed using an Ubuntu 20.04 LTS virtual machine running on VirtualBox on the same Lenovo as the previous dataset. This information is important because the latency for between both datasets are radically different, so it was necessary to give the disclaimer. 


# Part 1: Data Access Size

The experiment begins with testing the different data sizes to see how they affect throughput and latency. Seeing as this part of the project deals only with testing different batch sizes, we kept the ```iodepth``` variable fixed to the value of 1. Moreover, the ```numjobs``` variable was set to the value of 8, so the latency and bandwitdth are much higher than usual. This was intentionally done simply to show that the queueing theory is valid for high number of jobs. The command we ran was , ```fio --filename/dev/sdb --rw-randrw --direct=1 --bs=4K ==ioengine=sync --runtime=20 --numjobs=8 --time_based --group_reporting --name=speed_job --iodepth=1 --size=1048576```


As we increased the batch size from 4K to 128K, the throughput/bandwidth increased since the SSD is being utilized more and more. At the same time, the average latency was increasing, as predicted by the queuing theory. 

![](https://github.com/danielle-den/Project3/assets/143743140/d91db6ba-af47-4d66-ac06-dbddbf388149)    ![](https://github.com/danielle-den/Project3/blob/main/figures/1%20iodepth%20read%20Latency.png)

## Write
Those were the results of the ```--rw-read``` operation, so we decided to see how the SSD would fare when it came to the write operation. The expectation was for the queueing theory to still be followed, but with different magnitudes in throughput and latency. As the graphs below show, our expectations were correct and the trend of the previous graphs were realized here as well; as the batch sizes increased, the latency and throughput increased.

We realized also, that the IOPS was decreasing with the increase of the batch size. 

# Part 2: Read vs. Write Intensity Ratio
The general rule of thumb when designing products for customers is to create the product for the needs of the customer. In the case of SSDs, the designers must create them either with the assumptions that the consumer will perform more reads than writes, more writes than reads, or perhaps a bit of both. After testing the IOPS, latency and bandwidth of our Lenovo system, we were able to see that the designers probably had the idea of ... in mind. As can be seen from the graph below, the SSD had much better performance when the operations were reads only or write only. On the other hand when we performed the experiments skewed towards more reads than writes or even for 50:50, the bandwidth was much lower. 

![](https://github.com/danielle-den/Project3/blob/main/figures/read%20write%20ratio%20latency.png)


# Part 3: I/O Queue Depth
....

Furthermore, we tested varifying the **block size** against the **queue depth** with the expectation of the same trend as those seen before 





