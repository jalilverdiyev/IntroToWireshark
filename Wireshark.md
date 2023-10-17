# Intro to Wireshark

- Installing
	Go to https://www.wireshark.org/ and choose install.
- The basics: Profiles
	When you go to Edit->Configuration preferences, you can create, import, or export profiles. Profiles help you to use different modes for different purposes. For example, you may have different colors for Wi-Fi, but different ones for Bluetooth. For this purpose, you can create different profiles and use them whenever you want. Another plus is when you change your computer or OS, you can export your loved profile and import it on the new device. 
- Some useful settings:
	- For adjusting the layout, you can go to Edit->Preferences or ctrl+shift+p then choose the Layout section. In there, you can modify the layout.
	- Coloring rules, are useful if you want to add specific colors to your analysis. To achieve that, go to View->Coloring Rules, and it will open the default coloring rule. There you can change, add, or remove any rule. Pay attention to orders of rules, sometimes they can overload each other.
- Interface options:
	When you press the gear icon before starting to record, a new window will open, named: Capture Options. There you can customize what network interfaces you want to see and pick to record(or sniff;) ). If you come to the Output section, you can customize a few things:
	- The length of the output size.
	- The format of output
	- If you want you can apply some filters for example if the output size overflows 2mb then create(or save records) to new file.
	- Buffer ring. If you check this option and specify the number, you will tell the wireshark to return back first file if the file count is equal to the given number. Let's say you said that I want the ring buffer to be 5. Before you specified that if the output size overflows 2mb create a new file. Wireshark will continue to create new files once the output size overflows 2mb but after the fifth file, it will override the first and then the next, the next, and so on...
- Filtering:
	There are two types of filtering:
	- Capture filters
		Capture filters are useful for filtering the packet while capturing. For example, if you add filter tcp as the capture filter, then no packets that have any other protocols will be captured. So one must be very careful with it. To apply capture filter you just need to, <img src="Pasted image 20231017013041.png" /> 
		enter your filter here and then select your interface to start capturing packets.
	- Display filters
		However, display filters apply only for displaying which means that they kind don't block any packets, they just filter.
		Some famous display filters are:
		- Protocol filters like tcp, arp, ip, dns
			For ex <img src="Pasted image 20231017014343.png" />
		- Ip address filters like: ip.addr(both as source and destination), ip.dst(destination only), ip.src(source only)
		- Text filters like: frame contains(case insensitive) and frame matches(regex filtering)
		You can chain any amount of filters that you want by &&(and), ||(or). You can check if something equals in 2 ways: == or eq.
		If you have some problems memorizing filters, you can just use right-click filtering.
		If you have a specific filter and you want to make it a button so each time you click the filter will be applied, to do so you can use the + button after entering your filter:
		<img src="Pasted image 20231017015205.png"/>
		Then it will open 
		<img src="Pasted image 20231017015230.png" />
		this window where you can give it a name and description, also you can modify the filter itself.
	- Name resolution
		Name resolution is helpful to mask numbers with text(for better reading). To do so we should go to Edit->Preferences and in there Name Resolution section. We have different options to check or uncheck. If you check Resolve Transport Names: it will resolve well-known port numbers to human readable versions like port 443 will be https(443) which is quite good instead of 443. Then if you check the Resolve Network (IP) address, wireshark will rename all IP addresses with their domains. If you have the IP address of youtube in your pcap or pcapng file it will be renamed as youtube. And there could be some IP addresses that wireshark can't resolve like your local IP address. There you can right-click on that IP address then choose Edit Resolved Name and boom all rows will be affected.
- Statistics
		By default wireshark, offers tons of statistical tools. Like, Conversations, I/O Graphs even Geographical visualization(this needs an extra database). To use these tools you just have to go to Statistics and choose the tool that you want. If you want to use Geographical visualization here is a link below for a 4-minute video, which shows how to exactly make it happen:
		https://www.youtube.com/watch?v=IlVppluWTHw

Huge thanks to Chris Greer(PacketHead) and Networkchuck for helping to prepare this document. Here is a link to their channels:
[Chris Greer(PacketHead)](https://www.youtube.com/@ChrisGreer)
[Networkchuck](https://www.youtube.com/@NetworkChuck)
