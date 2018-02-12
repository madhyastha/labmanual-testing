---
title: IBIC to English Dictionary
sidebar: mydoc_sidebar
permalink: mydoc_dictionary.html
folder: mydoc
---

* **BIOSCRIBE** – A web database that stores data from the scanner (e.g. DICOMS), allowing collaborators to log in and download project data after it has been collected. This system is retired now and replaced by XNAT.

* **XNAT** – XNAT is a web database that stores neuroimaging data so that collaborators can securely download and upload shared data. XNAT succeeded BIOSCRIBE because it has a fully scriptable interface that you can use to download subject data. You can access [IBIC’s installation of XNAT.](https://xnatpro.ibic.washington.edu) [For more information see XNAT's home](http://www.xnat.org/).

* **IVAN** – Stands for IBIC’s Interoperable and Virtualized Analysis for Neuroimaging (IVAN) environment. The original concept of IVAN was to serve up a neuroimaging environment using virtual machines, permitting people to preserve complicated neuroimaging environments as software was updated and changed. However, with neurodebian it became easy to install multiple versions of software on the same machine. IVAN came to refer then to a specific workstation that users remotely logged in to, or to the IBIC gridengine cluster, at different times.

* **Evolution** – The name given to the first (and second) versions of a Linux-based neuroimaging software platform (based on Ubuntu 10.04, and later 12.04).

* **Devolution** – The name given to the third (and fourth) versions of a Linux-based neuroimaging software platform (based on Debian).

* **Revolution** – The name given to the latest version of a Linux-based neuroimaging software platform (based on Debian), running only on machines housed by UW IT.

* **S-10** – The name of a grant mechanism used to purchase a storage server, which used to be mounted on pole on /IBIC_S10_backup_2. Access to this device was slow, so it was primarily used for archive storage and backup. It was decomissioned in the beginning of 2016.

* **VDI** – Stands for Virtualized Desktop Interface, and refers to Sun Microsystems hardware acquired at the start of IBIC to support the IVAN environment (see above). This hardware has since been repurposed to different machines, including genu and sessionmanager.

* **eprime** – Is a software package (that runs on a PC) that allows you to create stimuli and tasks for fMRI experiments (like powerpoint, but with precise timing and synchronization with the scanner).

* **presentation** – Is a software package that allows you to create stimuli and tasks for fMRI experiments (like powerpoint, but with precise timing and synchronization with the scanner).


* **ldap** – Stands for [Lightweight directory Access
    Protocol](http://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol). This
    is the protocol used to allow IBIC machines to use your UW netid
    and password to access IBIC machines. Also used to manage UNIX
    group membership. This is why sometimes there is a delay between
    the time you are added to a new group and the time you can
    actually see the files on your computer.



* **neuron-class machine** – This is the nickname for the newest neuroimaging machines (e.g. neuron, adrc, tpp, panuc, etc.) They have 24 cores, 256GB memory, and up to 20TB RAID 10 storage. They are named after K-lab’s neuron.ibic.washington.edu, which was the first.

* **NAS** – This stands for “Network Attached Storage”, and is the storage for our home directories and much legacy data. It can be reached on directories /mnt/home, /project_space and /projects2.

* **NAS-II** – This is the second, less expensive NAS that is accessible on /NAS_II. Some Udall project data is stored there.

* **SGE, or gridengine** – The Sun Grid Engine (an old, open source version of what is now the proprietary Oracle Grid Engine) is a layer of software that allows you to run many jobs (programs) on multiple computers as if they belonged to one single large computer “cluster”. This is very important when doing neuroimaging; often it can take hours to process a single brain, and normally there are hundreds of jobs to perform, so using a cluster is much faster than running on your own workstation.

* **RedCAP** – Stands for Research Electronic Data Capture. This is a web database to be used for saving subject-specific study information. It is currently used for entering patient scanner demographics and log data, and supports convenient export of data into different formats.

(redcap.iths.org)

* **Udall** -- Short for the [Pacific Udall Center.](https://udallcenter.stanford.edu) (formerly the Pacific Northwest Udall Center). We have an imaging project that is part of this center of excellence for Parkinson Disease Research.

{% include links.html %}
