## Found Infrastructure

### Overview 
This is a hobby digital humanities project, designed to help me learn about distributed computing and datascience. Its 'distributed' scripts are run on an open hardware project comprising a 7 node Raspberry Pi / Rock64 cluster and an upcycled 2011 ThinkPad x230. Its 'standalone' scripts are generally run on a MacBook Pro.

Sources are downloaded from Project Gutenberg: works by Anthony Trollope. The 'acquire.ipynb' script might be able to be adapted for other authors but is currently designed for <a href="https://www.gutenberg.org/files/58383/58383-h/58383-h">Trollope's Gutenberg index page</a>. The 'clean.ipynb' might be more broadly useful. The <a href="https://pypi.org/project/gutenberg-cleaner/">gutenberg-cleaner</a> package is used for basic cleaning, with some additional code for content it doesn't catch. A significant amount of additional manual definition of strings is required to produce a clean corpus, added to /modules/scraps.py. I chose Trollope due to my literary-historical interest in him, but also because of his famously <a href="https://trollopesociety.org/trollope/his-writing/">massive output</a>. 

The https://www.dask.org framework is used for distributed computing. 

Recent stages of the project have made heavy use of the Microsoft Bing / OpenAI chatbot. All stages of the project have therefore made heavy use of Stack Overflow.

### Hardware
#### 'Distributed' 
The goal is to learn about distributed computing but also reuse and upcycle as much existing kit as possible. The project was started in the context of global supply-chain issues related to the Covid-19 pandemic, as well as increasingly bad news about the climate-change emergency. The Pi and networking equipment were bought new but the cluster could be considered to be cobbled together 'found' infrastructure. 

The total available compute power is: 53GB RAM, 28 cores. No GPU, although there might be ways to add it. I generally run 7 workers, including one on the primary ThinkPad node.

- 7 node Raspberry Pi + Rock64 + Lenovo ThinkPad cluster.
- 1x 2011 Lenovo ThinkPad Intel® Core™ i7-3520M CPU @ 2.90GHz × 4. Upcycled with flashed Skulls Coreboot; 1TB SSD; 16GB RAM. Pop!_OS 22.04 LTS.
- 5x Raspberry Pi 4 Model B Rev 1.4. Broadcom BCM2711, Quad core Cortex-A72 (ARM v8) 64-bit SoC @ 1.8GHz. 32GB MicroSD. 8GB SDRAM. Raspbian GNU/Linux 11 (bullseye).
- 1x ROCK64. Rockchip RK3328 Quad-Core ARM Cortex A53 64-Bit Processor. 16GB MicroSD. 4GB RAM. Armbian 23.02.2 Jammy with Linux 5.15.93-rockchip64.

- The cluster is connected via  an 8 port Netgear network switch and ethernet, as described in <a href="https://magpi.raspberrypi.com/articles/build-a-raspberry-pi-cluster-computer">this MagPi Magazine article</a> .
- The ThinkPad was flashed with Skulls, as described in this <a href="https://famicoman.com/2020/07/30/corebooting-the-thinkpad-x230-with-skulls">famicoman.com post</a>.

#### 'Standalone' 
- MacBook Pro: 13-inch, 2019, Four Thunderbolt 3 ports; Intel Iris Plus Graphics 655 1536 MB; 2.8 GHz Quad-Core Intel Core i7; 16 GB RAM; 1TB SSD. I might add the MacBook to the cluster in the future, when it is no longer my primary work machine.

### Current State / Future Goals
The state of the project varies between its standalone and distributed aspects. The former generally works quite well, the latter passes Hello World diagnostic tests but needs more debugging. The intention is to continue working on whatever needs to be fixed or methods I'd like to learn more about (data analysis, vizualization, distributed computing etc). Debugging and extending the standalone code is naturally much more straight-forward than debugging the distributed code + associated network / hardware infrastructure so that side of the project will probably move more slowly. 

Aside from being an aid to learning, part of the interest of the project for me is the comparison of standalone and cluster computing at this scale. So, for example, NLTK named entity recognition on a single merged file of Trollope's novels (Size on disk: 41.14 MB Word count: 7,965,030; Line count: 859,962; Title count: 67) takes 52m 48s on the MacBook Pro. Running the same NLTK entity extraction code against the individual titles on the Found Cluster it takes: TBD!! Such questions will be of questionable value to many people (technical or otherwise) but are interesting from the perspective of digital humanities and minimal computing.

<img src="assets/found_cluster.jpg" alt="Photo of Raspberry Pi cluster">
