# LFHStat

LFH stand for low fragment heap.
It's write by windbg script, and can stat the user block in LFH (busy or released).

Before LFH, heap manager(windows CRT) will create an heap entry for every call to new/malloc. It will layout like:

| _HEAP_ENTRY | user data |

LFH is default enable after windows vista, heap manager will create a chunk of heap entry for multiple call to new/malloc. It will layout like:

| _HEAP_ENTRY | _HEAP_USERDATA_HEADER | user data | ... | user data |

When one of user data is not released, the whole chunk of memory will not be released.
And this script will statistic how many block is released and how many is buzy in LFH.

LFH will disable in some condition:

*page heap is enable

*in debug mode

*the allocate size increase continuously

