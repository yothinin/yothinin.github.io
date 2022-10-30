The first article I would write is about how to resize the root size on CentOS. I have said I'm not an expert on anything but have had more experiments using Linux over a long time ago. I love to learn from more sources on the internet and books. Hence I need to record some experiences to remember in the future.

Last week, when came back from Nan province I read the Line group messages, I saw they have a problem with the disk full on the CentOS system. and they discuss to change its size at night.

Last night, they call me to ask for a consult from me, I give him this <a href="https://gist.github.com/troyfontaine/87091bd6a5c68f45dd62ced3d12bc377"> link</a> to fix it.

In a few minutes, he call me and tell me to re-installation the CentOS again I said to do that tomorrow.

This morning after I came to my desk. I connect to the server and check what he tries to do, he does the same as the step in the link's instruction but cannot complete it.

The structure of the disk volumes inside is: /root use 100% of 70GB /home use 3% of 1.8TB /swaps (I'm not sure of the number)

We need to delete /home and expand /root with the empty disk.

The problem is when he uses the command "lvremove /dev/cl/home" he encounters with "Logical volume vg/lv contains a filesystem in use."

Then he tries to use the lsof command to find the "process id" in used and kill it. It is not because that ID is used by the systems at the first boot.

I decided to edit the /etc/fstab to remove a mounting command from that file and reboot again without /home to mount. After that, I can use the lvremove command to remove the /home volume and can follow the instruction to expand the /root to 1.7 TB. What happens?

The problem was when you connect to the server by SSH client the system will read your profiles inside your home folder then you cannot remove the home volume. When you unmount it from the booting your connection cannot use any file in the /home, thus you can delete them.

Is it easy to fix it, right? I think so, that is easy to do but why does he cannot do this, because of the less experience to resolve the problem? I think he can do that the next day if he read these documents, that I want to tell him, but he doesn't ask me. How?

Thank you for reading and again if I use the wrong grammar or wrong language please correct me...
