# DLXOS-Dynamic-One-level-and-Two-Level-Paging

The goal of this project is to extend DLXOS memory management subsystem to support dynamic one-level page paging, 
dynamic two-level paging 

##Dynamic One level Paging 

>DLXOS currently supports a static one-level page table, which allocates a single 64KB page (for all of the code, data 
and the stack segment) per process. This page is allocated when the process is first created. The total amount of physical 
memory present in DLXSIM is 2 MB. Extended the current implementation to support dynamic one-level page tables. 
The system should totally support 512 pages of 4 KB each.During the process creation only the necessary physical pages 
(3 pages for text & data, one page for user stack) are allocated. The rest of the physical pages are dynamically allocated 
when a page fault occurs. Once a physical page is allocated, it is not freed. A process can use at most 32 physical pages 
(including the 4 pages allocated for text, data and user stack) during its execution. 
The kernel kills a process, if it exceeds the 32 page physical memory limit and displays an informative error message. 

##Dynamic Two level Paging 

>Extended the one-level dynamic page table implementation to support two-level dynamic page table. 
The virtual address space of each process is limited to 16MB. Any virtual address referenced by a process 
is translated to a physical address using the two-level page table. Each L1 (Level-1) page table entry refers to 
an L2(Level-2) page table and each L2 page table entry points to a 8KB page.  Each process can use at most 1 MB of
physical memory during its execution (this includes the pages being used for code & data, user stack, and L2 page tables). 
The kernel kills a process, if it exceeds the 1MB physical memory limit, and displays an informative error message
