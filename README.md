MINILAB 1.0

Setting up a MiniRack lab using MiniPCs has become a popular solution for both professionals and hobbyists who require a compact, powerful, and flexible computing environment. This blog post will explore the benefits and drawbacks of such a setup, with a focus on the Minisforum MS-01 and Ubiquiti Flex XG. We’ll delve into their features, performance, and use cases to help you make an informed decision. Additionally, we will discuss leveraging Nutanix Community Edition as the “AIO” operating system for the lab. We discussed this in previous posts, but we will show the power in a full cluster build, how simple it is to set up, operate and consume for both VMs and Containers as well as meeting your storage needs for your applications vs the other Home Lab OS’s out there.

Before we cover the Server and Networking hardware, let’s go over the mini-rack build itself. I decided to build my own vs buying one as I needed it to fit in a space with specific dimensions and needed it to be modular.

Here are the list of parts I chose:

4 x 7u Rack Rails: https://www.penn-elcom.com/us/7u-rack-strip-with-square-holes-1-16in-thick-r0863-2mm-07
3 x 1u 10″ Trays: https://deskpi.com/collections/new-arrival/products/deskpi
5 x 1u Blank Panels: https://deskpi.com/collections/new-arrival/products/deskpi-accessories-blank-pannel
1 x Cat6 12Port Keystone .5u Patch Panel: https://deskpi.com/collections/new-arrival/products/deskpi-rackmate-accessory-10-inch-network-switch
Nuts/Bolts/Washer kits from Lowes
Rackstuds: https://www.rackstuds.com/
Rubber Feet: https://www.rackstuds.com/
1u 10″ Rackmount custom made for the Ubiquiti Flex-XG Switch: https://shorturl.at/4yti7
All together the total was around $200.


A couple of things I didn’t like about this. First, the rack square hole spacing was off. I’m not sure if this was a defect from the factory or how these came. Because of this, and my usage of Rackstuds vs the typical rack nuts and screws, I had no choice but use the spacing I did which bothered me at first, but I then realized that this was ideal anyway for cooling and heat dissipation. Secondly, I definitely need a couple of more 1u blank panels on the side to firm this up on top which I already ordered, so I would recommend a total of 7 vs the 5 that are shown here. This will give it much more rigidity.

Advantages of a MiniRack Lab
Compact Size: MiniPCs are significantly smaller than traditional desktop PCs or servers, making them ideal for environments with limited space.
Power Efficiency: These devices generally consume less power, leading to lower energy costs and a reduced environmental impact.
Flexibility: MiniPCs can be easily reconfigured or upgraded, allowing for a scalable solution that can adapt to evolving needs.
Cost-Effective: They tend to be more affordable than full-sized servers, offering a cost-effective way to build a powerful lab environment.
Quiet Operation: Many MiniPCs are designed to operate quietly, which is beneficial in settings where noise is a concern.
Disadvantages of a MiniRack Lab
Limited Expandability: Due to their compact size, MiniPCs often have fewer expansion slots and upgrade options compared to full-sized servers.
Thermal Management: Smaller form factors can lead to heat dissipation challenges, potentially impacting performance under heavy loads.
Performance Constraints: While powerful, MiniPCs may not match the performance levels of high-end, full-sized servers, particularly for extremely demanding applications.
Spotlight on Minisforum MS-01
The Minisforum MS-01 is a standout in the realm of MiniPCs, offering a blend of performance and versatility.

Key Features
Processor: Equipped with a high-performance Intel 13900H 13th Gen Processor, the MS-01 is designed to handle a variety of computing tasks efficiently.
Memory and Storage: Supports up to 96GB of DDR5 5200 RAM and features multiple storage options, including M.2 NVMe and U.2 NVMe SSDs, providing ample room for data-intensive applications. In my case, each MS-01 contains 1 x Crucial P3 500GB NVMe SSD, 1 x 2TB Crucial P3 Plus NVMe SSD and a 2TB Solidigm P44 Plus Gen4 NVMe SSD. In order it’s AHV Boot, Data, CVM.
Connectivity: Offers a wide range of connectivity options, including USB 3.2, HDMI, DisplayPort, 2.5Gb/10Gb (SFP+) Ethernet and dual Thunderbolt 4, ensuring seamless integration with other devices and networks.
Expansion: PCI-E Gen5 x16 (x8 electrical) single slot AIC support. One MS-01 contains a single Tesla T4 GPU for AI Inference (to be replaced by an Nvidia L4)
Compact Design: Despite its powerful specs, the MS-01 maintains a compact and sleek design, making it ideal for a MiniRack setup. (a bit thicker than 1u)
Performance and Use Cases
The MS-01 excels in tasks such as virtualization, software development, and media streaming. Its robust processing power and flexible connectivity options make it suitable for building a versatile and responsive lab environment.

Spotlight on Ubiquiti Flex XG
The Ubiquiti Flex XG is a 10G switch designed to complement high-performance computing environments, such as a MiniRack lab.

Key Features
High-Speed Connectivity: Provides four 10Gb/one 1Gb Ethernet ports, ensuring high-speed data transfer and low latency, which are critical for demanding applications
Compact and Durable: Its compact form factor and durable construction make it suitable for both indoor and outdoor installations.
Managed Switch: Offers advanced management features, including VLAN support, link aggregation, and network monitoring, enabling efficient network management.
Power over Ethernet (PoE): Supports PoE, simplifying installation by reducing the need for separate power cables. (PoE is only supported to power switch, not on the ports themselves)
The network design is very straight forward since I already have a full Ubiquiti setup, which you can see here. Plugging this into the current setup, just adopted this device and I was off to the races. Having said that, if you need this in a more “stand alone” mode, you can simply run the Unifi Controller in a VM or Container on Nutanix Community Edition so you can get the MGMT interface back. The Switch will still work without the Controller being up after initial setup and configuration but if you need to have the control plane, you’ll need the Controller up.

You’ll see that I have different color Cat6 cables, the red is a single 1Gbe connection that I needed to leverage for my Xbox Series X, the three black are the 10GbE interfaces connected to my 10GBASE-T SFP+ to RJ45 Transceivers on the MS-01 and the white Cat6 is the trunk connected back to my 10GbE XG Switch which is also acting as an Aggregation Switch as well.

Performance and Use Cases
The Flex XG is ideal for scenarios requiring high bandwidth and low latency, such as data centers, research labs, and multimedia production environments. Its advanced management features and robust performance ensure a reliable and efficient network infrastructure for your MiniRack lab.

Leveraging Nutanix Community Edition
To further enhance your MiniRack lab, consider leveraging Nutanix Community Edition (CE). Nutanix CE is a free, community-supported version of Nutanix’s enterprise cloud platform, offering powerful tools for managing and deploying virtual environments.

Benefits of Nutanix Community Edition
Enterprise-Grade Virtualization: Nutanix CE provides a robust virtualization platform (AHV) that supports a wide range of workloads, from development and testing to production environments.
Hyperconverged Infrastructure: Combines storage, computing, and virtualization into a single solution, simplifying management and reducing hardware requirements.
Scalability: Easily scale your lab environment by adding more MiniPCs to your Nutanix cluster, allowing for flexible resource allocation and growth.
Simplified Management: The intuitive web-based interface makes it easy to manage and monitor your infrastructure, even for users with limited experience.
Community Support: Benefit from a vibrant community of users and developers who share insights, tips, and solutions for optimizing Nutanix CE.
Performance and Use Cases
Nutanix CE is ideal for building a high-performance, scalable, and resilient lab environment. It allows you to experiment with enterprise-grade features such as data protection, disaster recovery, and advanced networking, making it a valuable tool for learning and development. My use cases will be strictly Kubernetes. We will be running multiple different Kubernetes Distros from Suse (Rancher), RedHat (OpenShift) and finally our very own Nutanix Kubernetes Platform (NKP). Data Services will be provided by the HCI foundation AND another cluster running nested on my Proxmox server which I’ll cover next week. Data Services will include NDK locally, Files and S3 Objects as well as Nutanix Database Service (NDB) for structured data remotely on the nested CE cluster running on Proxmox. This cluster will also house the observability stack, again we’ll cover this in Part II next week.

Conclusion
Building a MiniRack lab with MiniPCs like the Minisforum MS-01, paired with network solutions such as the Ubiquiti Flex XG and powered by Nutanix Community Edition, offers a compact, cost-effective, and flexible solution for various computing needs. While there are some limitations to consider, the advantages often outweigh the drawbacks, particularly for small to medium-scale applications.

Whether you’re a professional looking to create a versatile lab environment or a tech enthusiast exploring the capabilities of compact computing, a MiniRack lab can provide the performance and flexibility you need. The Minisforum MS-01, Ubiquiti Flex XG, and Nutanix Community Edition are excellent choices to get started on this exciting journey.
