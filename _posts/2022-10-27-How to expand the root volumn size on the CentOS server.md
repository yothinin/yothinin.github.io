The first article I will write is about how to resize the root size on CentOS. I have said I’m not an expert on anything but have had more experiments using Linux over a long time ago. I love to learn from more sources on the internet and books. Hence, I need to record some experiences to remember in the future.

Last week, when I came back from Nan province, I read the Line group messages. I saw they have a problem with the full disk on the CentOS system, and they discussed how to change its size at night.

Last night, he called me to ask for a consultation from me. I gave him this <a href="https://gist.github.com/troyfontaine/87091bd6a5c68f45dd62ced3d12bc377">link</a> to fix it.

In a few minutes, he called me and told me to re-install CentOS again. I said to do that tomorrow.

This morning, I came to my desk. I connect to the server and check what he tries to do. He does the same as the step in the link’s instruction but cannot complete it.

The structure of the disk volumes inside is: /root use 100% of 70GB /home use 3% of 1.8TB /swaps (I’m not sure of the number)

<b>We need to delete /home and expand /root with the empty disk.</b>

The problem is when he uses the command “lvremove /dev/cl/home”, he encounters “Logical volume vg/lv contains a filesystem in use.”

Then he tries to use the lsof command to find the “process id” in used and kill it. It is not because ID is used by the systems at the first boot.

<b>I decided to edit the /etc/fstab to remove a mounting command from that file and reboot again without /home to mount.</b> After that, I can use the lvremove command to remove the /home volume and can follow the instruction to expand the /root to 1.7 TB. What happens?

The problem was, when you connect to the server by SSH client, the system will read your profile inside your home folder, then you cannot remove the home volume. When you unmount it from booting, your connection cannot use any file in the /home, thus you can delete them.

Is it easy to fix it, right? I think that is easy to do, but why can't he do this, because of the less experience to resolve the problem? I think he can do that the next day if he reads this document that I want to tell him, but he doesn’t ask me. How?

Thank you for reading and, again, if I use the wrong grammar or wrong language please correct me…
