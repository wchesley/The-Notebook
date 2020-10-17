# Network Security and Data Communications

#### WTAMU CIDM-3385

# Table of Contents: 
- [Chapter 5 IP Addressing](#Chapter-5-IP-Addressing)
- [Chapter 6 Switch Management](#Chapter-6-Switch-Management)
- [Chapter 7 Routing](#Chapter-7-Routing)
- [Chapter 8 Firewalls](#Chapter-8-Firewalls)

# Chapter 5 IP Addressing
###### [Back to top](#-Table-of-Contents)
<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>What is an octet?</li>
      <li>What is the decimal equivalent of the following binary number? 01100111. What is the binary equivalent of the following
      decimal number? 211.</li>
      <li>How is the network portion of an IP address identified?</li>
      <li>Which portion of a class C address designates the network address?</li>
      <li>What is the difference between subnetting and supernetting? Which method uses a subnet mask that is longer than the
      default subnet mask?</li>
      <li>What does /14 mean in the following IP address: 199.78.11.12/14?</li>
      <li>How does variable-length subnet masking work<i>?</i></li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure IP addresses.</li>
      <li>Configure IP addresses on mobile devices.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">IANA</td>
      <td class="content">The Internet Assigned Numbers Authority is a function of a nonprofit private American corporation that
      oversees global IP address allocation, autonomous system number allocation, root zone management in the Domain Name System,
      media types, and other Internet Protocol-related symbols and internet numbers.</td>
    </tr>
    <tr>
      <td class="centered">Classful IP Addresses</td>
      <td class="content">
        Classful addresses are IP addresses that use a default subnet mask, as follows:
        <ul>
          <li>Class A: 255.0.0.0</li>
          <li>Class B: 255.255.0.0</li>
          <li>Class C: 255.255.255.0</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td class="centered">VLSM</td>
      <td class="content">Variable Length Subnet Masking (VLSM) is the method used to divide an IP address into subnets of
      different sizes. When using VLSM, you ignore the default subnet mask boundaries and specify a custom number of subnet mask
      bits.</td>
    </tr>
    <tr>
      <td class="centered">Subnetting</td>
      <td class="content">The process of dividing a large network into smaller networks.</td>
    </tr>
    <tr>
      <td class="centered">Supernetting</td>
      <td class="content">The process of combining two or more networks.</td>
    </tr>
    <tr>
      <td class="centered">Classless Inter-Domain Routing<br>
      (CIDR)</td>
      <td class="content">A set of internet protocol standards used to create unique identifiers for networks and host
      devices.</td>
    </tr>
    <tr>
      <td class="centered">ANDing</td>
      <td class="content">The process used to determine the network address/ID.</td>
    </tr>
    <tr>
      <td class="centered">Subnet Mask</td>
      <td class="content">A 32-bit number that defines which portion of an IPv4 address identifies the network address and which
      portion of the address defines the host address.</td>
    </tr>
    <tr>
      <td class="centered">Network ID</td>
      <td class="content">A 32-bit number that identifies the network an IPv4 address belongs to.</td>
    </tr>
  </tbody></table>

  <p>This section helps you prepare for the following certification exam objectives:</p>

  <table class="objectives" border="1">
    <tbody><tr class="header">
      <td class="centered" width="260">Exam</td>
      <td class="contentheader">Objective</td>
    </tr>
    <tr>
      <td class="centered" width="260">TestOut Network Pro</td>
      <td class="content">2.1 Configure IP addressing, DNS, and DHCP for a network host.</td>
    </tr>
    <tr>
      <td class="centered">CompTIA Network+</td>
      <td class="content">
        <p>1.3 Explain the concepts and characteristics of routing and switching.</p>
        <ul>
          <li>Properties of network traffic
            <ul>
              <li>Broadcast</li>
            </ul>
          </li>
        </ul>
        <p>1.4 Given a scenario, configure the appropriate IP addressing components.</p>
        <ul>
          <li>Subnet mask</li>
          <li>Subnetting
            <ul>
              <li>Classful
                <ul>
                  <li>Classes A, B, C, D, and E</li>
                </ul>
              </li>
              <li>Classless
                <ul>
                  <li>VLSM</li>
                  <li>CIDR notation (IPv4 vs. IPv6)</li>
                </ul>
              </li>
              <li>Address assignments
                <ul>
                  <li>DHCP</li>
                  <li>Static</li>
                </ul>
              </li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
  </tbody></table>
</div>
<div id="TextViewer-root" class="TextViewer-root">
<h3 style="color: #F96302">IP Addresses</h3>

  <p>IP addresses allow hosts to participate on IP-based networks. The following 
	are important things to know about IP addresses:</p>

  <ul>
    <li>An IP address is a 32-bit binary number represented as four octets (four 
	8-bit-numbers). Each octet is separated by a period.</li>
    <li>IP addresses can be represented two different ways:
      <ul>
        <li>Decimal (e.g., 131.107.2.200). In decimal notation, each octet must 
		be between 0 and 255.</li>
        <li>Binary (e.g., 10000011.01101011.00000010.11001000). In binary 
		notation, each octet is an 8-character number.</li>
      </ul>
    </li>
    <li>To convert from binary to decimal, memorize the decimal equivalent to 
	the following binary numbers:
      <table>
        <tbody>
          <tr class="header">
            <td class="centered">10000000</td>
            <td class="centered">01000000</td>
            <td class="centered">00100000</td>
            <td class="centered">00010000</td>
            <td class="centered">00001000</td>
            <td class="centered">00000100</td>
            <td class="centered">00000010</td>
            <td class="centered">00000001</td>
          </tr>
          <tr>
            <td class="centered">128</td>
            <td class="centered">64</td>
            <td class="centered">32</td>
            <td class="centered">16</td>
            <td class="centered">8</td>
            <td class="centered">4</td>
            <td class="centered">2</td>
            <td class="centered">1</td>
          </tr>
        </tbody>
      </table>Add together the decimal values of each bit position with a 1 
	value. For example, the decimal equivalent of 10010101 is:<br>
      128 + 16 + 4 + 1 = 149 
    </li>
    <li>The IP address includes both the network and the host address.</li>
    <li>A subnet mask is a 32-bit number associated with an IP address that 
	identifies the network portion of the address. In binary form, the subnet 
	mask is always a series of 1s followed by a series of 0s (1s and 0s are 
	never mixed in sequence in the mask). A simple mask might be 255.255.255.0 
	(i.e., 11111111.11111111.11111111.00000000).</li>
    <li>IP addresses have a default <i>class</i>. The address class identifies 
	the range of IP addresses and the default subnet mask used for the range. 
	The following table shows the default address class for each IP address 
	range:
      <table>
        <tbody>
          <tr class="header">
            <td class="centered">Class</td>
            <td class="contentheader">Address Range</td>
            <td class="centered">First Octet Range</td>
            <td class="centered">Default Subnet Mask</td>
          </tr>
          <tr>
            <td class="centered">A</td>
            <td class="content">1.0.0.0 to 126.255.255.255</td>
            <td class="centered">1–126<br>
            (00000001–01111110 binary)</td>
            <td class="centered">255.0.0.0</td>
          </tr>
          <tr>
            <td class="centered">B</td>
            <td class="content">128.0.0.0 to 191.255.255.255</td>
            <td class="centered">128–191<br>
            (10000000–10111111 binary)</td>
            <td class="centered">255.255.0.0</td>
          </tr>
          <tr>
            <td class="centered">C</td>
            <td class="content">192.0.0.0 to 223.255.255.255</td>
            <td class="centered">192–223<br>
            (11000000–11011111 binary)</td>
            <td class="centered">255.255.255.0</td>
          </tr>
          <tr>
            <td class="centered">D</td>
            <td class="content">224.0.0.0 to 239.255.255.255</td>
            <td class="centered">224–239<br>
            (11100000–11101111 binary)</td>
            <td class="centered">n/a</td>
          </tr>
          <tr>
            <td class="centered">E</td>
            <td class="content">240.0.0.0 to 255.255.255.255</td>
            <td class="centered">240–255<br>
            (11110000–11111111 binary)</td>
            <td class="centered">n/a</td>
          </tr>
        </tbody>
      </table>
    </li>
    <li>When using the default subnet mask for an IP address, you have the 
	following number of subnet addresses and hosts per subnet:
      <ul>
        <li>There are only 126 Class A network IDs (most of these addresses are 
		already assigned). Each class A address gives you 16,777,214 hosts per 
		network.</li>
        <li>There are 16,384 Class B network IDs. Each class B address gives you 
		65,534 hosts per network.</li>
        <li>There are 2,097,152 Class C network IDs. Each class C address gives 
		you 254 hosts per network.</li>
        <li>Class D addresses are used for multicast groups rather than network 
		and host IDs.</li>
        <li>Class E addresses are reserved for experimental use.</li>
      </ul>
    </li>
  </ul>

  <h3 style="color: #F96302">Special Considerations</h3>
  
  <p>As you are assigning IP addresses to hosts, think of the following special 
	considerations:</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Address</td>
        <td class="contentheader">Consideration</td>
      </tr>
      <tr>
        <td class="centered">Network</td>
        <td class="content">
          The first address in an address range is used to identify the network 
			itself. For the network address, the host portion of the address 
			contains all 0s. For example:
          <ul>
            <li>Class A network address: 115.0.0.0</li>
            <li>Class B network address: 154.90.0.0</li>
            <li>Class C network address: 221.65.244.0</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Broadcast</td>
        <td class="content">
          The last address in the range is the broadcast address, and it is used 
			to send messages to all hosts on the network. In binary form, the 
			broadcast address has all 1s in the host portion of the address. For 
			example, assuming the default subnet masks are used:
          <ul>
            <li>115.255.255.255 is the broadcast address for network 115.0.0.0</li>
            <li>154.90.255.255 is the broadcast address for network 154.90.0.0</li>
            <li>221.65.244.255 is the broadcast address for network 221.65.244.0</li>
          </ul>
          <blockquote class="info">
            The broadcast address might also be designated by setting each of 
			the network address bits to 0. For example, 0.0.255.255 is the 
			broadcast address of a Class B address. This designation means "the 
			broadcast address for this network."
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Host Addresses</td>
        <td class="content">
          When you are assigning IP addresses to hosts, understand the 
			following:
          <ul>
            <li>Each host must have a unique IP address.</li>
            <li>Each host on the same network must have an IP address with a 
			common network portion of the address. You must use the same subnet 
			mask when configuring addresses for hosts on the same network.</li>
          </ul>The range of IP addresses available for network hosts is 
			identified by the subnet mask and/or the address class. When 
			assigning IP addresses to hosts, be aware that you cannot use the 
			first or last addresses in the range (these are reserved for the 
			network and broadcast addresses respectively). For example:
          <ul>
            <li>For the class A network address 115.0.0.0, the host range is 
			115.0.0.1 to 115.255.255.254.</li>
            <li>For the class B network address 154.90.0.0, the host range is 
			154.90.0.1 to 154.90.255.254.</li>
            <li>For the class C network address 221.65.244.0, the host range is 
			221.65.244.1 to 221.65.244.254.</li>
          </ul>
          <blockquote class="info">
            Another way to identify a host on a network is to set the network 
			portion of the address to all 0s. For example, the address 
			0.0.64.128 means "host 64.128 on this network."
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Local Host</td>
        <td class="content">Addresses in the 127.0.0.0 range are reserved to 
		refer to the local host (the host you're currently working at). The most 
		commonly used address is 127.0.0.1, which is the loopback address.</td>
      </tr>
    </tbody>
  </table>

  <p>Because IP addresses assigned to hosts must be unique, the use of IP 
	addresses on the internet is controlled by organizations that ensure that 
	every organization is given its own range of IP addresses to assign to 
	hosts:</p>
  <ul>
    <li>The Internet Assigned Numbers Authority (IANA) manages the assignment of 
	IP addresses on the internet. IANA is operated by the Internet Corporation 
	for Assigned Names and Numbers (ICANN).</li>
    <li>IANA allocates blocks of IP addresses to Regional Internet Registries 
	(RIRs). An RIR has authority over IP addresses in a specific region of the 
	world.</li>
    <li>An RIR assigns blocks of addresses to Internet Service Providers (ISPs).</li>
    <li>An ISP assigns one or more IP addresses to individual computers or 
	organizations connected to the Internet.</li>
  </ul>
</div>
</br>

## Subnetting
<div id="TextViewer-root" class="TextViewer-root">
  <p><i>Subnetting</i> is the process of dividing a large network into smaller 
	networks called <i>subnets</i>. When you subnet a network, each network 
	segment has a different network address, or subnet address. In practice, the 
	terms network and subnet are used interchangeably to describe a physical 
	network segment with a unique network address.</p>
<h3 style="color: #F96302">Functions of Subnetting</h3>
<p>From a physical standpoint, subnetting is necessary because network 
architectures impose a limit on the number of hosts allowed on a single network 
segment. As your network grows, you will need to create subnets (physical 
networks) to:</p>

  <ul>
    <li>Increase the number of devices that can be added to the LAN (to overcome 
	the architecture limits)</li>
    <li>Decrease the number of devices on a single subnet (to reduce traffic 
	congestion)</li>
    <li>Reduce the processing load placed on computers and routers</li>
    <li>Isolate sensitive systems on the network</li>
  </ul>

  <p>Subnetting is also used to efficiently allocate available IP addresses. For 
	example, an organization with a class B network ID is allocated enough 
	addresses for 65,536 hosts. However, if the organization in practice uses 
	only 10,000 of those host IDs, over 55,000 IP addresses are going unused. 
	Subnetting provides a way to break the single class B network ID into 
	multiple smaller network IDs.</p>

  <ul>
    <li>Subnetting uses custom subnet masks instead of the default subnet masks 
	(e.g., using 255.255.255.0 with a Class B address instead of the default 
	255.255.0.0).</li>
    <li>When you subnet a network by using a custom mask, you can divide the IP 
	addresses between several subnets. However, you also reduce the number of 
	hosts available on each network.</li>
    <li>Using custom subnet masks is often called <i>classless</i> addressing 
	because the subnet mask cannot be inferred simply from the class of a given 
	IP address. The address class is ignored, and the mask is always supplied to 
	identify the network and host portions of the address.</li>
  </ul>

  <p>The following table shows how a Class B address can be subnetted to provide 
	additional subnet addresses. Notice that by using a custom subnet mask, the 
	Class B address looks like a Class C address.</p>
<h3 style="color:#F96302">Subnetting Class B Addresses</h3>

  <table>
    <tbody>
      <tr class="header">
        <td></td>
        <td class="centered">Default Example</td>
        <td class="centered">Custom Example</td>
      </tr>
      <tr>
        <td class="leftheader">Network Address</td>
        <td class="centered">188.50.0.0</td>
        <td class="centered">188.50.0.0</td>
      </tr>
      <tr>
        <td class="leftheader">Subnet Mask</td>
        <td class="centered">255.255.0.0</td>
        <td class="centered">255.255.255.0</td>
      </tr>
      <tr>
        <td class="leftheader"># of Subnet Addresses</td>
        <td class="centered">One</td>
        <td class="centered">254</td>
      </tr>
      <tr>
        <td class="leftheader"># of Hosts per Subnet</td>
        <td class="centered">65,534</td>
        <td class="centered">254 per subnet</td>
      </tr>
      <tr>
        <td class="leftheader">Subnet Address(es)</td>
        <td class="centered">188.50.0.0 (only one)</td>
        <td class="centered">188.50.1.0<br>
        188.50.2.0<br>
        188.50.3.0<br>
        (and so on)</td>
      </tr>
      <tr>
        <td class="leftheader">Host Address Range(s)</td>
        <td class="centered">188.50.0.1 to 188.50.255.254</td>
        <td class="centered">188.50.1.1 to 188.50.1.254<br>
        188.50.2.1 to 188.50.2.254<br>
        188.50.3.1 to 188.50.3.254<br>
        (and so on)</td>
      </tr>
    </tbody>
  </table>

  <p>Remember that the last valid host address ends with 254 because 255 is a 
	broadcast address and is not available as a host address. For example:</p>

  <ul>
    <li>For the class A network address 115.0.0.0, the host range is 115.0.0.1 
	to 115.255.255.254.</li>
    <li>For the class B network address 154.90.0.0, the host range is 154.90.0.1 
	to 154.90.255.254.</li>
    <li>For the class C network address 221.65.244.0, the host range is 
	221.65.244.1 to 221.65.244.254.</li>
  </ul>

  <blockquote class="info">
    While subnetting divides a large address space into multiple subnets, <i>
	supernetting</i> combines multiple small network addresses into a single 
	larger network. Supernetting allows multiple Class C addresses to be 
	combined into a single network.
  </blockquote>
</div>

## Variable Length Subnet Masking (VLSM)

<div id="TextViewer-root" class="TextViewer-root">
<h3 style="color: #F96302">Classful IP Addresses</h3>

  <p><i>Classful</i> addresses are IP addresses that use a default subnet mask, 
	as follows:</p>

  <ul>
    <li>Class A: 255.0.0.0</li>
    <li>Class B: 255.255.0.0</li>
    <li>Class C: 255.255.255.0</li>
  </ul>
  
  <p>They are considered classful because the default subnet mask identifies the 
	network portion and host portion of the IP address.</p>

<h3 style="color: #F96302">Classless IP Addresses</h3>
 
 <p>Classless addresses, on the other hand, use a custom mask value to separate 
	the network and host portions of the IP address. Classless addressing is 
	made possible using Classless Inter-Domain Routing (CIDR). CIDR allows you 
	to use only part of an octet for the network address. This is called <i>
	partial subnetting</i>, or <i>variable-length subnet masking</i> (VLSM).</p>

  <h3 style="color: #F96302">VLSM</h3>
  
  <p>When using VLSM, you ignore the default subnet mask boundaries and specify 
	a custom number of subnet mask bits. For example, you could define a subnet 
	mask of 255.255.252.0. In addition to the first and second octets, this mask 
	also assigns the first six bits in the third octet to be used for the 
	network portion of the address. This mask would appear in binary notation as 
	follows:</p>

  <p>11111111.11111111.11111100.00000000</p>

  <p>As you can see, the six bits are reallocated from the host address to the 
	network address. This allows you to create additional subnets, but it 
	reduces the number of host addresses available within each one.</p>

  <p>For example, suppose your network is composed of four separate physical 
	network segments connected by routers. The network uses the 10.0.0.0 private 
	IP addressing scheme, but you want to divide the 10.0.0.0 network into four 
	separate subnets. Under classful addressing, this network would use the 
	first octet for the network address and the last three octets for node 
	addresses. However you need to divide this large network into four subnets. 
	To do this, you need to reconfigure the subnet mask to include the first two 
	bits of the second octet, creating four additional networks. Instead of 
	using the default Class A subnet mask of 11111111.00000000.00000000.00000000 
	(255.0.0.0), you use a subnet mask of 11111111.11000000.00000000.00000000 
	(255.192.0.0). Using CIDR notation, you can specify a prefix of <b>/10</b> 
	to indicate you are using 10 bits for the subnet mask.</p>

  <p>The following are four possible values in the IP address for the two extra 
	bits that have been added to the subnet mask:</p>

  <ul>
    <li>00 = 0</li>
    <li>01 = 64</li>
    <li>10 = 128</li>
    <li>11 = 192</li>
  </ul>

  <p>These values define the lower and upper boundaries for the four subnets 
	created by the classless subnet mask, as shown in the following table:</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="contentheader">Subnet Address</td>
        <td class="contentheader">Subnet Mask</td>
        <td class="contentheader">Subnet Host Address Range</td>
        <td class="contentheader">Subnet Broadcast Address</td>
      </tr>
      <tr>
        <td class="content">10.0.0.0</td>
        <td class="content">255.192.0.0</td>
        <td class="content">10.0.0.1–10.63.255.254</td>
        <td class="content">10.63.255.255</td>
      </tr>
      <tr>
        <td class="content">10.64.0.0</td>
        <td class="content">255.192.0.0</td>
        <td class="content">10.64.0.1–10.127.255.254</td>
        <td class="content">10.127.255.255</td>
      </tr>
      <tr>
        <td class="content">10.128.0.0</td>
        <td class="content">255.192.0.0</td>
        <td class="content">10.128.0.1–10.191.255.254</td>
        <td class="content">10.191.255.255</td>
      </tr>
      <tr>
        <td class="content">10.192.0.0</td>
        <td class="content">255.192.0.0</td>
        <td class="content">10.192.0.1–10.255.255.254</td>
        <td class="content">10.255.255.255</td>
      </tr>
    </tbody>
  </table>

  <blockquote class="info">
    On the internet, you can access many subnet calculators&nbsp; to calculate 
	subnet boundaries, host addresses, and broadcast addresses.
  </blockquote>
</div>

## IP Address Assignment

<div id="TextViewer-root" class="TextViewer-root">
  <p>The following table lists several options for assigning IP addresses.</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Method</td>
        <td class="contentheader">Uses</td>
      </tr>
      <tr>
        <td class="centered">Dynamic Host Configuration Protocol (DHCP)</td>
        <td class="content">
          A DHCP server is a special server configured to pass out IP addresses 
			and other IP configuration information to network clients. DHCP 
			servers ensure that each client is assigned a unique IP address.
          <ul>
            <li>When a DHCP client system boots, it contacts the DHCP server for IP configuration information. The DHCP server is
            configured with a range of IP addresses it can assign to hosts. These ranges are called scopes.
              <ul>
                <li>The DHCP server can be configured to prevent specific addresses in the range from being assigned to clients.
                This is called an exclusion.</li>
                <li>You can also configure a DHCP server to deliver the same address to a specific host each time it requests an
                address. This is called a reservation.</li>
              </ul>
            </li>
            <li>The DHCP server can also be configured to pass out other IP configuration information, such as the default gateway
            and DNS server addresses.</li>
            <li>The DHCP server assigns the IP address and other information to the client. The assignment is called a
            <i>lease</i>, and it includes a lease time that identifies how long the client can use the IP address.
              <ul>
                <li>Periodically, the client contacts the DHCP server to renew the lease on the IP address. The client will also
                attempt to renew the lease on the same IP address if it reboots.</li>
                <li>The DHCP lease process uses broadcast frames at Layer 2. For this reason, DHCP requests do not pass through
                routers to other subnets by default. To enable DHCP broadcasts between subnets, enable IP helper or DHCP relay on
                the appropriate routers.</li>
                <li>When the lease expires, the DHCP server releases the reserved IP address. This is known as 
				the expired IP
                address.</li>
              </ul>
            </li>
            <li>Any client configured to use DHCP can get an IP address from any server configured for DHCP, regardless of its
            operating system.</li>
          </ul>
          <blockquote class="info">
            DHCP is the preferred IP configuration method for small, medium, and large networks.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Static (Manual) Assignment</td>
        <td class="content">
          Static addressing means that IP configuration information is manually configured on each host. Static addressing is best
          used in the following situations:
          <ul>
            <li>On networks with a very small number of hosts.</li>
            <li>On networks that do not change often or that will not grow.</li>
            <li>To permanently assign IP addresses to hosts that must always have the same address (such as printers, servers, or
            routers).</li>
            <li>For hosts that cannot accept IP addresses from DHCP servers.</li>
            <li>To reduce DHCP-related traffic.</li>
          </ul>
          <blockquote class="info">
            Static addressing is very susceptible to configuration errors and duplicate IP address configuration errors. Static
            addressing disables both APIPA and DHCP functions on the host.
          </blockquote>
        </td>
      </tr>
    </tbody>
  </table>
</div>

## APIPA and Alternate IP Addressing

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>How do you know if a host is using an APIPA address?</li>

      <li>Which IP configuration parameters are set when APIPA is used? Which parameters are not set?</li>

      <li>In which scenarios would an alternate IP configuration simplify IP configuration?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Set Up alternate addressing.</li>

      <li>Configure alternate addressing.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Automatic Private IP Addressing (APIPA)</td>
      <td class="content">APIPA provides an option for automatic IP address assignment without a DHCP server. APIPA is enabled by
      default on most modern operating systems, including Windows and Linux.</td>
    </tr>
    <tr>
      <td class="centered">Alternate IP Configuration</td>
      <td class="content">A manual configuration of a computer's IP address, 
		default gateway, DNS server address, and WINS address. This 
		configuration is used if the DHCP server fails to provide this similar 
		information.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>If a host is configured to obtain its IP address from a DHCP server but 
	that server is unreachable, then an alternate IP address assignment method 
	may be employed as follows:</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Method</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Automatic Private IP Addressing (APIPA)</td>
        <td class="content">
          APIPA provides an option for automatic IP address assignment without a 
			DHCP server. APIPA is enabled by default on most modern operating 
			systems, including Windows and Linux.
          <p>Using APIPA, hosts can assign themselves an IP address on the 
			169.254.0.0 network (with a mask of 255.255.0.0) if they can't 
			locate a DHCP server. If a network host is configured to use dynamic 
			IP addressing and a DHCP server can't be contacted, APIPA assigns a 
			temporary IP address to the host. However, only the IP address and 
			mask are assigned. Default gateway and DNS server addresses are not 
			assigned. For this reason, APIPA can be used only to enable 
			communications within a single subnet. Communication with other 
			networks, including the internet, are not possible. In addition, 
			communication with network infrastructure devices that use static IP 
			addressing, such as servers, is not possible even if they are on the 
			same local subnet as the APIPA host.</p>
        </td>
      </tr>
      <tr>
        <td class="centered">Alternate IP Configuration</td>
        <td class="content">With an alternate IP configuration, static IP 
		configuration values are used if a DHCP server cannot be contacted. When 
		you configure an alternate IP address, APIPA is automatically disabled. 
		It is recommended that you use an IP configuration other than APIPA 
		because you hosts need to access other systems on the local subnet and 
		on other networks, including the internet. Alternate IP configuration 
		also allows continued access to servers and other network infrastructure 
		devices that use static IP addresses.</td>
      </tr>
    </tbody>
  </table>
</div>

## DHCP Server Configuration

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>What type of configuration parameters can be delivered using DHCP?</li>
      <li>What are the advantages of static IP address assignments?</li>
      <li>When might you want to use static IP addressing?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure a DHCP server.</li>
      <li>Configure DHCP options.</li>
      <li>Create DHCP exclusions.</li>
      <li>Create DHCP client reservations.</li>
      <li>Configure a DHCP client.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">DHCP Discover (D)</td>
      <td class="content">The client begins by sending out a DHCP Discover frame to identify DHCP servers on the network.</td>
    </tr>
    <tr>
      <td class="centered">DHCP Offer (O)</td>
      <td class="content">A DHCP server that receives a Discover request from a client responds with a DHCP Offer advertisement,
      which contains an available IP address. If more than one DHCP server responds with an offer, the client usually responds to
      the first offer it receives.</td>
    </tr>
    <tr>
      <td class="centered">DHCP Request (R)</td>
      <td class="content">The client accepts the offered IP address by sending a DHCP request back to the DHCP 
		server.</td>
    </tr>
    <tr>
      <td class="centered">DHCP ACK (A)</td>
      <td class="content">The DHCP server responds to the request by sending a DHCP ACK (acknowledgement). At this point, the IP
      address is leased to and configured on the DHCP client.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>The dynamic host configuration protocol (DHCP) centralizes management of IP addressing in a network by allowing a server to
  dynamically assign IP addresses to clients. DHCP also allows mobile users, who move from network to network, to easily obtain an
  IP address appropriate for each network they connect to.</p>

<h3 style="color:#F96302">Obtain an Address from a DHCP Server</h3>

<p>Because a DHCP client doesn't have an IP address when it initially boots, it must use broadcast frames to communicate with
  a DHCP server. The table below describes the method used to obtain an address from a DHCP 
server.</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Broadcast</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">DHCP Discover (D)</td>
        <td class="content">The client begins by sending out a DHCP Discover frame to identify DHCP servers on the network.</td>
      </tr>
      <tr>
        <td class="centered">DHCP Offer (O)</td>
        <td class="content">A DHCP server that receives a Discover request from a client responds with a DHCP Offer advertisement,
        which contains an available IP address. If more than one DHCP server responds with an offer, the client usually responds to
        the first offer that it receives.</td>
      </tr>
      <tr>
        <td class="centered">DHCP Request (R)</td>
        <td class="content">The client accepts the offered address by sending a DHCP 
		request back to the DHCP server. If multiple
        offers were sent, the DHCP request message from the client also informs the other DHCP servers that their offers were not
        accepted and the IP addresses contained in their offers can be made available to other clients.</td>
      </tr>
      <tr>
        <td class="centered">DHCP ACK (A)</td>
        <td class="content">The DHCP server responds to the request by sending a DHCP ACK (acknowledgement). At this point, the IP
        address is leased to and configured on the DHCP client.</td>
      </tr>
    </tbody>
  </table>

  <blockquote class="info">
    If the DHCP server is on a different subnet, additional configuration 
	steps are required, since network routers drop the DHCP broadcast frames by default.
  </blockquote>

<h3 style="color:#F96302">Configuring a DHCP Server</h3>

<p>Keep in mind the following when configuring a DHCP Server:</p>

  <ul>
    <li>The DHCP service needs to auto-start when the server boots.</li>
    <li>The server must have a static IP address.</li>
    <li>A MAC reservation is an association of a MAC address with a specific IP address. In other words, the client with the
    specified MAC address is assigned the same IP address each time it requests an address.</li>
    <li>An IP reservation means you program MAC addresses into the DHCP server. When the DHCP server sees a certain host requesting
    an IP address based on its MAC, it will give you a specific IP address.</li>
  </ul>

  <p>For a DHCP server to deliver IP addresses, it must have a scope configured. A <i>scope</i> is the range of IP addresses that
  the DHCP server can assign to clients. A scope can also be called a <i>pool</i>. When working with scopes, remember the
  following:</p>

  <ul>
    <li>There should be only one scope per network segment.</li>
    <li>The scope must be activated before the DHCP server can assign addresses to clients. After you activate a scope, you should
    not change it.</li>
    <li>A scope has a subnet mask that determines the subnet for a given IP address. You cannot change the subnet mask of an
    existing DHCP scope; to change the subnet mask used by a scope, you must delete and recreate the scope.</li>
    <li>Lease duration values are part of the scope properties, and they determine the length of time a client can use an IP
    address leased through DHCP.</li>
  </ul>

  <blockquote class="info">
    The DHCP server can also be configured with exclusions, which are specific addresses in the range that should not be assigned.
  </blockquote>

<h3 style="color:#F96302">DHCP Server Functions</h3>

<p>In addition to providing IP addresses, a DHCP server can also provide clients with additional IP configuration parameters
  using <i>options</i>. Commonly used DHCP options include the subnet mask, the 
	default gateway address, and a DNS server address. The following levels of options can be configured:</p>
  <ul>
    <li>Server options are applied to all computers that get an IP address from the DHCP 
	server, regardless of which scope they obtain the address from (for example, if your organization has only one DNS server, then all DHCP clients need the same DNS server
    address.)</li>
    <li>Scope options are applied to all computers that get an IP address from a particular scope on the DHCP 
	server (for example,
    because scopes are associated with specific subnets, each scope needs to be configured with the appropriate default gateway
    address option.)</li>
    <li>Client options are applied to a specific DHCP client. The client's MAC address is used to identify which system
    receives the option.</li>
  </ul>

  <p>The DHCP console provides context-sensitive icons to reflect DHCP server status as follows:</p>

  <ul>
    <li>A check mark in a green circle indicates that the DHCP server is connected and authorized.</li>
    <li>A red down arrow indicates that the DHCP server is connected, but not authorized.</li>
    <li>A horizontal white line inside a red circle indicates that the DHCP server is connected, but the current user does not have
    the administrative credentials necessary to manage the server.</li>
    <li>An exclamation point inside a yellow triangle indicates that 90% of available addresses for server scopes are either in use
    or leased.</li>
    <li>An exclamation point inside a blue circle indicates that 100% of available addresses for server scopes are either in use or
    leased.</li>
  </ul>
</div>

## DHCP Relay

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>
  <div class="discussion">
    <ul>
      <li>What is the difference between an RFC 1542 compliant router and a DHCP relay agent?</li>
    </ul>
    <p>In this section, you will learn to:</p>
    <ul>
      <li>Configure a DHCP relay agent</li>
      <li>Add a DHCP server on another subnet</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">RFC 1542 Compliant Router</td>
      <td class="content">An RFC 1542 compliant router listens for DHCP traffic and routes any received DHCP frames to the
      appropriate subnet. .</td>
    </tr>
    <tr>
      <td class="centered">DHCP Relay Agent</td>
      <td class="content">A function of the Routing and Remote Access service (RRAS) 
		role on a Windows server, the DHCP Relay Agent service sends the DHCP 
		packets it receives to a remote DHCP server on a different subnet.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>Because a DHCP client doesn't have an IP address assigned when it initially 
	boots, it must use broadcast frames to communicate with a DHCP server. If 
	the server is on a different subnet than the client, then the DHCP requests 
	sent by the client will not reach the server because broadcast frames are 
	dropped by network routers. If your network is configured in this manner, 
	you can implement one of the following mechanisms to forward DHCP broadcasts 
	through network routers to a remote DHCP server on a different subnet:</p>

  <table border="1">
    <tbody><tr class="header">
      <td class="centered">Option</td>
      <td class="contentheader">Description</td>
    </tr>
    <tr>
      <td class="centered">RFC 1542 Compliant Router</td>
      <td class="content">
        An RFC 1542 compliant router listens for DHCP traffic and routes any 
		received DHCP frames to the appropriate subnet. For example, on a Cisco 
		router, you can enable this functionality by using the <b>ip 
		helper-address</b> command. The syntax is:
        <blockquote class="code">
          ip helper-address <i>[server_address]</i>
        </blockquote>Replace <i><b>[server_address]</b></i> with the IP address 
		of the remote DHCP server.
      </td>
    </tr>
    <tr>
      <td class="centered">DHCP Relay Agent</td>
      <td class="content">
        If you use a Windows server in your network, then you can install the 
		Routing and Remote Access service (RRAS) role on the server and enable 
		the DHCP Relay Agent Role service. The DHCP Relay Agent service sends 
		the DHCP packets it receives to a remote DHCP server on a different 
		subnet. To configure the DHCP Relay service, you must:
        <ul>
          <li>Specify which server network interface the agent listens on for 
			DHCP messages.</li>
          <li>Specify the IP address of the remote DHCP server the agent should 
			forward DHCP messages to.</li>
        </ul>
      </td>
    </tr>
  </tbody></table>
</div>

## DNS Name Resolution

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>How are host names organized in DNS?</li>
      <li>What is the difference between a forward lookup zone and a reverse lookup?</li>
      <li>What is the role of the root servers in DNS?</li>
      <li>In DNS, what is the difference between a zone and a domain?</li>
      <li>What is the difference between an A record and a PTR record?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure DNS addresses.</li>
      <li>Create standard DNS zones.</li>
      <li>Create reverse DNS zones.</li>
      <li>Create host records.</li>
      <li>Create CNAME records.</li>
      <li>Troubleshoot DNS records.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">. (dot) domain</td>
      <td class="content">The . (dot) domain, or root domain, denotes a fully qualified, unambiguous domain name.</td>
    </tr>
    <tr>
      <td class="centered">Top-Level Domain<br>
      (TDL)</td>
      <td class="content">The last part of a domain name (for example, .com, .edu, .gov). TDLs are managed by
      the Internet Corporation of Assigned Names and Numbers (ICANN).</td>
    </tr>
    <tr>
      <td class="centered">Fully Qualified Domain Name<br>
      (FQDN)</td>
      <td class="content">The host name and all domain names separated by periods.
      The final period (which is for the root domain) is often omitted and only implied.</td>
    </tr>
    <tr>
      <td class="centered">Additional Domains</td>
      <td class="content">Additional domains are second-level domains with names registered to an individual or organization for
      use on the internet. These names are based on an appropriate top-level domains, depending on the type of organization or
      geographic location where a name is used. Yahoo.com and microsoft.com are examples of additional domains in your DNS
      structure.</td>
    </tr>
    <tr>
      <td class="centered">Hostname</td>
      <td class="content">The hostname is the part of a domain name that represents a specific host. For example, "www"
      is the hostname of www.example.com.</td>
    </tr>
    <tr>
      <td class="centered">Records</td>
      <td class="content">Records are used to store entries for hostnames, IP addresses, and other information in the zone
      database. Each host has at least one record in the DNS database that maps the hostname to the IP address.</td>
    </tr>
    <tr>
      <td class="centered">Authoritative Server</td>
      <td class="content">An authoritative server is a DNS server that has a complete copy of all the records for a particular
      domain.</td>
    </tr>
    <tr>
      <td class="centered">Dynamic DNS<br>
      (DDNS)</td>
      <td class="content">DDNS enables clients or the DHCP server to update records in the zone database. Without dynamic updates,
      all A (host) and PTR (pointer) records must be configured manually. With dynamic updates, host records are created and
      deleted automatically whenever the DHCP server creates or releases an IP address lease.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>The Domain Name System (DNS) is a hierarchical distributed database that 
	maps logical host names to IP addresses. DNS is a distributed database 
	because no one server holds all of the DNS information. Instead, multiple 
	servers hold portions of the data as follows:</p>

  <ul>
    <li>Each division of the database is held in a zone database file.</li>
    <li>Zones typically contain one or more domains, although additional servers 
	might hold information for child domains.</li>
    <li>DNS servers hold zone files and process name resolution requests from 
	client systems.<br>
&nbsp;</li>
  </ul>

  <p><font color="#FF6300"><span style="font-size: 11pt; font-weight: 700">Parts 
	of a DNS</span></font><br>
	The DNS is made up of the following components:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Component</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">. (dot) domain</td>
        <td class="content">The . (dot) domain, or <i>root</i> domain, denotes a 
		fully qualified, unambiguous domain name.</td>
      </tr>
      <tr>
        <td class="centered">Top-Level Domain (TLD)</td>
        <td class="content">A TLD is the last part of a domain name (for 
		example, .com, .edu, .gov). TLDs are managed by the Internet Corporation 
		of Assigned Names and Numbers (ICANN).</td>
      </tr>
      <tr>
        <td class="centered">Fully Qualified Domain Name (FQDN)</td>
        <td class="content">The FQDN includes the host name and all domain names 
		separated by periods. The final period (which is for the root domain) is 
		often omitted and only implied.</td>
      </tr>
      <tr>
        <td class="centered">Additional Domains<br>
        (Second-Level Domains)</td>
        <td class="content">Additional domains are second-level domains with 
		names registered to an individual or organization for use on the 
		internet. These names are based on an appropriate top-level domain, 
		depending on the type of organization or geographic location where a 
		name is used. Yahoo.com and microsoft.com are examples of additional 
		domains in your DNS structure.</td>
      </tr>
      <tr>
        <td class="centered">Host Name</td>
        <td class="content">The host name is the part of a domain name that 
		represents a specific host. For example, "www" is the host name of 
		www.example.com.</td>
      </tr>
      <tr>
        <td class="centered">Records</td>
        <td class="content">
          <i>Records</i> are used to store entries for host names, IP addresses, 
			and other information in the zone database. Each host has at least 
			one record in the DNS database that maps the host name to the IP 
			address. Common resource records include:
          <ul>
            <li>The A (Host Address) record maps an IPv4 (32-bit) DNS host name 
			to an IP address. This is the most common resource record type.</li>
            <li>The AAAA (Quad-A) record maps an IPv6 (128-bit) DNS host name to 
			an IP address.</li>
            <li>The PTR (Pointer) record maps an IP address to a host name (by 
			pointing to an A record).</li>
            <li>The MX (Mail Exchanger) record identifies servers that can be 
			used to deliver email.</li>
            <li>The CNAME (Canonical Name) record provides alternate names (or 
			aliases) to hosts that already have a host record. If you only use a 
			single A record with multiple CNAME records, when the IP address 
			changes, you only have to modify the A record.</li>
            <li>The NS (Name Server) resource record identifies all name servers 
			that can perform name resolution for the zone. Typically, there is 
			an entry for the primary server and all secondary servers for the 
			zone (all authoritative DNS servers).</li>
            <li>The SRV (Service Locator) record identifies the resources that 
			provide a service. This allows clients to find services, such as 
			domain controllers, through DNS. Windows automatically creates these 
			records as needed.</li>
            <li>The SPF (Sender Policy Framework) record identifies authorized 
			email servers. SPF records are created using TXT records. DNS uses 
			the SPF record to verify that the host that sent the mail is 
			authorized to use the DNS name.</li>
            <li>DKIM (Domain Keys Identified Mail) is an email authentication 
			method that uses a digital signature to validate email and make it 
			easier to identify spoofed emails. The sending mail server signs the 
			email with the private key, and the receiving mail server uses the 
			public key in the domain's DNS information to verify the signature. 
			One domain can have several DKIM keys publicly listed in DNS, but 
			each matching private key is only on one mail server. DKIM records 
			are created using TXT records.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Authoritative Server</td>
        <td class="content">An <i>authoritative server</i> is a DNS server that 
		has a complete copy of all the records for a particular domain.</td>
      </tr>
      <tr>
        <td class="centered">Dynamic DNS (DDNS)</td>
        <td class="content">
          DDNS enables clients or the DHCP server to update records in the zone 
			database. Without dynamic updates, all A (host) and PTR (pointer) 
			records must be configured manually. With dynamic updates, host 
			records are created and deleted automatically whenever the DHCP 
			server creates or releases an IP address lease. Dynamic updates 
			occur when:
          <ul>
            <li>A network host's IP address is added, released, or changed.</li>
            <li>The DHCP server changes or renews an IP address lease.</li>
            <li>The client's DNS information is manually changed using <b>
			ipconfig /registerdns</b>.</li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>

  <p><font color="#FF6300"><span style="font-size: 11pt"><b>Recursion Process</b></span></font><br>
	When you use the host name of a computer (for example, if you type a URL 
	such as www.mydomain.com), recursion is employed to find the IP address. <i>
	Recursion</i> is the process by which a DNS server uses root name servers 
	and other DNS servers to perform name resolution. The following steps occur:</p>

  <ol>
    <li>The host looks in its local cache to see if it has recently resolved the 
	host name.</li>
    <li>If the information is not in the cache, it checks the Hosts file. The 
	Hosts file is a static text file that contains host-name-to-IP address 
	mappings.</li>
    <li>If the IP address is not found, the host contacts its preferred DNS 
	server. If the preferred DNS server can't be contacted, the host continues 
	contacting additional DNS servers until one responds.</li>
    <li>The host sends the name information to the DNS server. The DNS server 
	checks its cache and Hosts file. If the information is not found, the DNS 
	server checks any zone files that it holds for the requested name.</li>
    <li>If the DNS server can't find the name in its zones, it forwards the 
	request to a root zone name server. This server returns the IP address of a 
	DNS server that has information for the corresponding top-level domain (such 
	as .com).</li>
    <li>The first DNS server requests the information from the top-level domain 
	server. The server returns the address of a DNS server with the information 
	for the next highest domain. This process continues until a DNS server is 
	contacted that holds the necessary information.</li>
    <li>The DNS server places the information in its cache and returns the IP 
	address to the client host. The client host also places the information in 
	its cache and uses the IP address to contact the desired destination device.</li>
  </ol>

  <p><font color="#FF6300"><span style="font-size: 11pt"><b>DNS Facts</b></span></font><br>
	The following are some additional facts about DNS:</p>

  <ul>
    <li>A forward lookup finds the IP address for a given host name. A <i>
	reverse lookup</i> finds the host name from a given IP address.</li>
    <li>Root DNS servers hold information for the root zone ( . ). Root servers 
	answer name resolution requests by supplying the address of the 
	corresponding top-level DNS server (servers authoritative for .com, .edu, 
	and similar domains).</li>
    <li>On very small networks, you could configure a HOSTS file with several 
	entries to provide limited name resolution services. However, you would have 
	to copy the HOSTS file to each client. The work involved in this solution is 
	only suitable for temporary testing purposes or for overriding information 
	that might be received from a DNS server.</li>
    <li>On the client, you should configure a list of DNS suffixes you want to 
	append to unqualified DNS names submitted by clients for resolution as 
	follows:
      <ul>
        <li>Configure a single DNS suffix for clients using a DHCP option on the 
		DHCP server.</li>
        <li>Configure multiple suffixes by adding them to the client manually. </li>
      </ul>
    </li>
  </ul>
</div>

## IPV-6

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>What is the primary reason for developing IPv6?</li>
      <li>How many hexadecimal numbers are in an IPv6 address? How does this compare to a MAC address?</li>
      <li>What do you add to an IPv6 address when you remove one or more quartets with all 0s?</li>
      <li>What information is included within the IPv6 address prefix?</li>
      <li>How many numbers are used for the interface ID? How can the interface ID be related to the MAC address?</li>
      <li>What is the difference between ISATAP and 6to4 tunneling?</li>
      <li>What is the difference between stateful autoconfiguration and stateless autoconfiguration?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure IPv6 addresses.</li>
      <li>Configure a DHCP6 server.</li>
      <li>Configure an IPv6 address.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Global-Unicast</td>
      <td class="content">An IPv6 address type that is publicly routable and can be used in the internet.</td>
    </tr>
    <tr>
      <td class="centered">Unique-Local</td>
      <td class="content">An IPv6 address type that indicates an IP address is a private IP address.</td>
    </tr>
    <tr>
      <td class="centered">Link-Local</td>
      <td class="content">An IPv6 address type that indicates that the IP address was configured by default.</td>
    </tr>
    <tr>
      <td class="centered">Multicast</td>
      <td class="content">An IPv6 address type that indicates that the packet is addressed to a number of hosts on the network, but
      not all hosts.</td>
    </tr>
    <tr>
      <td class="centered">Prefix ID</td>
      <td class="content">The leftmost bits of the IPv6 address, also know as the network ID. The prefix is used for routing IPv6
      packets.</td>
    </tr>
    <tr>
      <td class="centered">Interface ID</td>
      <td class="content">The rightmost bits of the IPv6 address used to uniquely identify a network card (interface) in a
      host.</td>
    </tr>
    <tr>
      <td class="centered">Anycast</td>
      <td class="content">A unicast address that is assigned to more than one interface, typically 
		interfaces belonging to different hosts.</td>
    </tr>
    <tr>
      <td class="centered">Local Loopback</td>
      <td class="content">The local loopback address for the local host is 0:0:0:0:0:0:0:1 (also identified as ::1 or ::1/128). The
      local loopback address is not assigned to an interface. It can verify that the TCP/IP protocol stack is properly installed on
      the host.</td>
    </tr>
    <tr>
      <td class="centered">Dual Stack</td>
      <td class="content">A dual stack configuration enables a host to 
		communicate with IPv4 and IPv6 hosts; the IPv4 and IPv6 protocol stacks 
		run concurrently on a host.</td>
    </tr>
    <tr>
      <td class="centered">Tunneling</td>
      <td class="content">
        Tunneling allows IPv6 hosts or sites to communicate over the existing IPv4 infrastructure. A device encapsulates IPv6
        packets within IPv4 packets for transmission across an IPv4 network, and then the IPv6 packets are de-encapsulated by
        another device at the other end.
        </td>
    </tr>
    <tr>
      <td class="centered">Static Full Assignment</td>
      <td class="content">The entire 128-bit address and all other configuration information is statically assigned to the
      host.</td>
    </tr>
    <tr>
      <td class="centered">Static Partial Assignment</td>
      <td class="content">The prefix is statically assigned. The interface ID is derived from the MAC address.</td>
    </tr>
    <tr>
      <td class="centered">Stateless Autoconfiguration</td>
      <td class="content">Clients automatically generate the interface ID and learn the subnet prefix and default gateway through
      the Neighbor Discovery Protocol (NDP).</td>
    </tr>
    <tr>
      <td class="centered">DHCPv6</td>
      <td class="content">
        IPv6 uses an updated version of DHCP, DHCPv6. It operates in two modes, 
		stateful and stateless.
        </td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>The addresses available under the current IPv4 addressing standard have 
	been exhausted. In response to this situation, a new IP addressing system 
	(IP version 6, or IPv6) has been developed. An IPv6 address is a 128-bit 
	binary number. A sample IPv6 IP address looks like the following: 
	35BC:FA77:4898:DAFC:200C:FBBC:A007:8973.</p>

  <h3 style="color: #F96302">Features of an IPv6 Address</h3>
  
  <p>The following list describes the features of an IPv6 address:</p>

  <ul>
    <li>It is made up of 32 hexadecimal numbers organized into 8 quartets.</li>
    <li>The quartets are separated by colons.</li>
    <li>Each quartet is represented as a hexadecimal number between 0 and FFFF. 
	Each quartet represents 16 bits of data (FFFF = 1111 1111 1111 1111).</li>
    <li>Leading zeros can be omitted in each section. For example, the quartet 
	0284 could also be written as 284.</li>
    <li>An address with consecutive zeros can be expressed more concisely by 
	substituting a double colon for the group of zeros. For example:
      <ul>
        <li>FEC0:0:0:0:78CD:1283:F398:23AB</li>
        <li>FEC0::78CD:1283:F398:23AB (concise form)
          <blockquote class="info">
            This is also called address compression. Address compression is when 
			you take a fully-notated IPv6 address and remove empty octets from 
			it, replacing them with a colon.
          </blockquote>
        </li>
      </ul>
    </li>
    <li>If an address has more than one consecutive location where one or more 
	quartets are all zeros, only one location can be abbreviated. For example, 
	FEC2:0:0:0:78CA:0:0:23AB can be abbreviated as:
      <ul>
        <li>FEC2::78CA:0:0:23AB<br>
        or</li>
        <li>FEC2:0:0:0:78CA::23AB<br>
        but not</li>
        <li>FEC2::78CA::23AB</li>
      </ul>
    </li>
    <li>The 128-bit address contains two parts:
      <table>
        <tbody>
          <tr class="header">
            <td class="centered">Component</td>
            <td class="contentheader">Description</td>
          </tr>
          <tr>
            <td class="centered">Prefix</td>
            <td class="content">
              The first 64 bits are known as the <i>prefix</i>.
              <ul>
                <li>The prefix can be divided into various parts that identify 
				things such as geographic region, the ISP, the network, and the 
				subnet.</li>
                <li>The <i>prefix length</i> identifies the number of bits in 
				the relevant portion of the prefix. To indicate the prefix 
				length, add a slash (/) followed by the prefix length number. 
				Full quartets with trailing 0s in the prefix address can be 
				omitted (e.g., 2001:0DB8:4898:DAFC::<b>/</b>64).</li>
                <li>Because addresses are allocated based on physical location, 
				the prefix generally identifies the location of the host. The 
				64-bit prefix is often referred to as the <i>global routing</i> 
				prefix.</li>
              </ul>
            </td>
          </tr>
          <tr>
            <td class="centered">Interface ID</td>
            <td class="content">
              The last 64 bits are known as the <i>interface ID</i>. This is the 
				unique address assigned to an interface.
              <ul>
                <li>Addresses are assigned to interfaces (network connections), 
				not to the host. Technically, the interface ID is not a host 
				address.</li>
                <li>In most cases, individual interface IDs are not assigned by 
				ISPs but are rather generated automatically or managed by site 
				administrators.</li>
                <li>Interface IDs must be unique within a subnet, but they can 
				be the same if they are on different subnets.</li>
                <li>On Ethernet networks, the interface ID can be automatically 
				derived from the MAC address. Using the automatic host ID 
				simplifies administration.</li>
              </ul>
              <p>To ensure that the interface ID is unique for every host on the 
				network, IPv6 uses the Extended Unique Identifier 64 (EUI-64) 
				format. The following are some details of the EUI-64 format:</p>
              <ul>
                <li>Each host has a unique 48-bit hardware address called a <i>
				MAC address</i> (also called the <i>burned-in</i>
                address) that is assigned to each device by the vendor. The MAC 
				address is guaranteed to be unique through design. The EUI-64 
				format uses the unique MAC address by:
                  <ol>
                    <li>Splitting the MAC address into 24-bit halves.</li>
                    <li>Inserting 16 bits (represented by hex FFFE) between the 
					two halves.
                      <blockquote class="info">
                        For example, a host with a MAC address of 
						20-0C-FB-BC-A0-07 would start with the following EUI-64 
						interface ID: 200C:FB<span class="c1"><b>FF</b>:<b>FE</b></span>BC:A007.
                      </blockquote>
                    </li>
                    <li>To be complete, the EUI-64 format requires setting the 
					seventh bit in the first byte to binary 1 (reading from left 
					to right, this is the second hex value in the interface ID). 
					This bit is called the
                    <i>universal/local (U/L) bit</i>.
                      <ul>
                        <li>When the U/L bit is set to 0, the MAC address is a 
						burned-in MAC address.</li>
                        <li>When the U/L bit is set to 1, the MAC address has 
						been configured locally. EUI-64 requires the U/L bit to 
						be set to 1.</li>
                      </ul>Review the following examples:
                      <ul>
                        <li>200C:FBFF:FEBC:A007 (Incorrect interface ID, as the 
						U/L bit is still set to 0)</li>
                        <li>220C:FBFF:FEBC:A007 (Correct interface ID)</li>
                      </ul>
                    </li>
                  </ol>
                </li>
              </ul>
            </td>
          </tr>
        </tbody>
      </table>
    </li>
  </ul>

  <p>IPv6 adds the following features not included in IPv4:</p>

  <table>
    <tbody><tr class="header">
      <td class="centered">Feature</td>
      <td class="contentheader">Description</td>
    </tr>
    <tr>
      <td class="centered">Auto-configuration</td>
      <td class="content">Because hardware IDs are used for node IDs, IPv6 nodes 
		simply need to discover their network IDs. This can be done by 
		communicating with a router.</td>
    </tr>
    <tr>
      <td class="centered">Built-in Quality of Service</td>
      <td class="content">Built-in support for bandwidth reservations makes 
		guaranteed data transfer rates possible. (Quality of service features 
		are available as add-ons within an IPv4 environment but are not part of 
		the native protocol.)</td>
    </tr>
    <tr>
      <td class="centered">Built-in Security Features</td>
      <td class="content">IPv6 has built-in support for security protocols such 
		as IPsec. (IPsec security features are available as add-ons within an 
		IPv4 environment.)</td>
    </tr>

    <tr>
      <td class="centered">Source Intelligent Routing</td>
      <td class="content">IPv6 nodes have the option to include addresses that 
		determine part or all of the route a packet will take through the 
		network.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>IPv6, assigns addresses to interfaces (network connections). All interfaces 
	require an IPv6 address, and each interface can have more than one IPv6 
	address. IPv6 defines the following types of addresses:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Address Type</td>
        <td class="contentheader" colspan="2">Description</td>
      </tr>
      <tr>
        <td class="centered" rowspan="4">Unicast</td>
        <td class="content" colspan="2">
          <i>Unicast</i> addresses are assigned to a single interface for the 
			purpose of allowing one host to send and receive data. Packets sent 
			to a unicast address are delivered to the interface identified by 
			that address.
          <p>There are three types of unicast IPv6 addresses:</p>
        </td>
      </tr>
      <tr>
        <td class="centered">Link-local</td>
        <td class="content">
          <i>Link-local</i> addresses (also known as <i>local link</i> 
			addresses) are only valid on the current subnet. Details include the 
			following:
          <ul>
            <li>Link-local addresses have an FE80::/10 prefix. This includes any 
			address beginning with FE8, FE9, FEA, or FEB.</li>
            <li>All nodes must have at least one link-local address, although 
			each interface can have multiple addresses.</li>
            <li>Link-local addresses are used for automatic address 
			configuration, for neighbor discovery, or for subnets that have no 
			routers.</li>
          </ul>
          <blockquote class="info">
            Do not use link-local IPv6 addressing on routed networks. Routers 
			never forward packets destined for link-local addresses to other 
			subnets.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Unique local</td>
        <td class="content">
          <i>Unique local</i> addresses are private addresses used for 
			communication within a site or between a limited number of sites. In 
			other words, unique local addressing is commonly used for network 
			communications that do not cross a public network; they are the 
			equivalent of private addressing in IPv4. Details include the 
			following:
          <ul>
            <li>Because unique local addresses are not registered with IANA, 
			they cannot be used on a public network without address translation.</li>
            <li>Addresses beginning with a prefix of FC00 or FD00 are unique 
			local addresses.</li>
            <li>Following the prefix, the next 40 bits are used for the Global 
			ID. The Global ID is generated randomly, creating a high probability 
			of uniqueness on the entire internet.</li>
            <li>Following the Global ID, the remaining 16 bits in the prefix are 
			used for subnet information.</li>
            <li>Unique local addresses are likely to be globally unique, but 
			they are not globally routable. Unique local addresses might be 
			routed between sites by a local ISP.</li>
          </ul>
          <p>The process for designing a network addressing scheme when using 
			unique local addresses is similar to that used for global unicast 
			addresses. The key difference is how the prefix is defined. Because 
			the address range is not registered, a global routing prefix does 
			not have to be requested from an ISP. Instead, each organization 
			defines its own prefix.</p>
        </td>
      </tr>
      <tr>
        <td class="centered">Global unicast</td>
        <td class="content">
          <i>Global unicast</i> addresses are assigned to individual interfaces 
			that are globally unique. All IPv6 addresses that aren't 
			specifically reserved for other purposes are defined as global 
			unicast addresses. The global routing prefix assigned to an 
			organization by an ISP is typically 48 bits long (/48), but it could 
			be as short as /32 or as long as /56, depending on the ISP. All 
			subnet IDs within the same organization must begin with the same 
			global routing prefix, but they must also be uniquely identified 
			using a different value in the subnet field.
          <p>Using this addressing scheme allows organizations to define a large 
			number (2<sup>16</sup>) of IPv6 subnets. When you design an IPv6 
			network, define separate IPv6 subnets by the following:</p>
          <ul>
            <li>Network segments separated by routers</li>
            <li>VLANs</li>
            <li>Point-to-point WAN links</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Multicast</td>
        <td class="content" colspan="2">
          <i>Multicast</i> addresses represent a dynamic group of hosts. Packets 
			sent to a multicast address are sent to all interfaces identified by 
			that address. If different multicast addresses are used for 
			different functions, only the devices that need to participate in a 
			particular function will respond to the multicast; devices that do 
			not need to participate in the function will ignore the multicast. 
			Details include the following:
          <ul>
            <li>All multicast addresses have an FF00::/8 prefix.</li>
            <li>Multicast addresses that are restricted to the local link have 
			only an FF02::/16 prefix. Packets starting with FF02 are not 
			forwarded by routers.</li>
            <li>Multicast addresses with an FF01::/16 prefix are restricted to a 
			single node.</li>
          </ul>The following are well-known multicast addresses:
          <ul>
            <li>FF02::1 is for all nodes on the local link. This is the 
			equivalent of the IPv4 subnet broadcast address. FF01::1 is for all 
			interfaces on a node.</li>
            <li>FF02::2 is for all routers on the local link. FF01::2 is for all 
			routers on node-local.</li>
            <li>FF02::1:2 is for all DHCP servers or DHCP relay agents on the 
			local link. DHCP relay agents forward these packets to other 
			subnets.</li>
          </ul>
          <blockquote class="info">
            There are no broadcast addresses in IPv6. IPv6 multicast addresses 
			are used instead of broadcast addresses.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Anycast</td>
        <td class="content" colspan="2">
          The <i>anycast</i> address is a unicast address that is assigned to 
			more than one interface, typically belonging to different hosts. An 
			anycast packet is routed to the nearest interface having that 
			address (based on routing protocol decisions). Details include the 
			following:
          <ul>
            <li>An anycast address is the same as a unicast address. Assigning 
			the same unicast address to more than one interface makes it an 
			anycast address.</li>
            <li>You can have a link-local, unique local, or global unicast 
			anycast address.</li>
            <li>When you assign an anycast address to an interface, you must 
			explicitly identify the address as an anycast address to distinguish 
			it from a unicast address.</li>
            <li>Anycast addresses can be used to locate the nearest server of a 
			specific type (for example, the nearest DNS or network time server).</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Loopback</td>
        <td class="content" colspan="2">The local loopback address for the local 
		host is 0:0:0:0:0:0:0:1 (also identified as ::1 or ::1/128). The local 
		loopback address is not assigned to an interface. It can verify that the 
		TCP/IP protocol stack is properly installed on the host.</td>
      </tr>
    </tbody>
  </table>
</div>

## IPv4 to IPv6 Migration

<div id="TextViewer-root" class="TextViewer-root">
  <p>The worldwide transition from IPv4 to IPv6 will be a long process. Although 
	IPv6 is not yet widely adopted, you can implement it if your systems support 
	it. As the implementation of IPv6 proceeds, there will be times when 
	compatibility with IPv4 will be necessary. </p>
	<h3 style="color:#F96302">IPv6 Deployment Strategies</h3>
<p>The following table lists various strategies for deploying IPv6.</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Method</td>
        <td class="contentheader" colspan="2">Description</td>
      </tr>
      <tr>
        <td class="centered">Dual Stack</td>
        <td class="content" colspan="2">A <i>dual stack</i> configuration 
		enables a host to communicate with IPv4 and IPv6 hosts; the IPv4 and 
		IPv6 protocol stacks run concurrently on a host. IPv4 is used to 
		communicate with IPv4 hosts, and IPv6 is used to communicate with IPv6 
		hosts. When dual stack is implemented on hosts, intermediate routers and 
		switches must also run both protocol stacks.</td>
      </tr>
      <tr>
        <td class="centered" rowspan="6">Tunneling</td>
        <td class="content" colspan="2">
          <i>Tunneling</i> allows IPv6 hosts or sites to communicate over the 
			existing IPv4 infrastructure. A device encapsulates IPv6 packets 
			within IPv4 packets for transmission across an IPv4 network, and 
			then the IPv6 packets are de-encapsulated by another device at the 
			other end.
          <p>Tunneling solutions include the following:</p>
        </td>
      </tr>
      <tr>
        <td class="content">Manually Configured tunnel</td>
        <td class="content">
          In this configuration, tunnel endpoints are configured as 
			point-to-point connections between devices. Because of the time and 
			effort required for configuration, use manually configured tunnels 
			only when you have a small number of sites that need to connect 
			through the IPv4 internet or when you want to configure secure 
			site-to-site associations. Manual tunneling:
          <ul>
            <li>Is configured between routers at different sites.</li>
            <li>Requires dual stack routers as the tunnel endpoints, but is 
			compatible with IPv6-only hosts. </li>
            <li>Works through NAT.</li>
            <li>Uses a static association of an IPv6 address to the IPv4 address 
			of the destination tunnel endpoint.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="content">6-to-4 Tunneling</td>
        <td class="content">
          With 6-to-4 tunneling, tunneling endpoints are configured 
			automatically between devices. Use 6-to-4 tunneling to dynamically 
			connect multiple sites through the IPv4 internet. Because of its 
			dynamic configuration, 6-to-4 tunneling is easier to administer than 
			manual tunneling. 6-to-4 tunneling:
          <ul>
            <li>Is configured between routers at different sites.</li>
            <li>Requires dual stack routers as the tunnel endpoints, but can 
			work with IPv6-only hosts.</li>
            <li>Works through NAT.</li>
            <li>Uses a dynamic association of an IPv6 site prefix to the IPv4 
			address of the destination tunnel endpoint.</li>
            <li>Automatically generates an IPv6 address for the site using the 
			2002::/16 prefix followed by the public IPv4 address of the tunnel 
			endpoint router. For example, a router with an IPv4 address of 
			207.142.131.202 would serve the site with the following prefix: 
			2002:CF8E:83CA::/48 (CF8E:83CA is the hexadecimal equivalent of 
			207.142.131.202).</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="content">4-to-6 Tunneling</td>
        <td class="content">4-to-6 tunneling works in a manner similar to 6-to-4 
		tunneling. However, instead of tunneling IPv6 traffic through an IPv4 
		network, 4-to-6 tunnels IPv4 traffic through an IPv6 network by 
		encapsulating IPv4 packets within IPv6 packets.</td>
      </tr>
      <tr>
        <td class="content">Intra-site Automatic Tunnel Addressing Protocol 
		(ISATAP)</td>
        <td class="content">
          The intra-site automatic tunnel addressing protocol is a tunneling 
			method that provides IPv6 communication over a private IPv4 network. 
			ISATAP tunneling:
          <ul>
            <li>Is configured between individual hosts and an ISATAP router.</li>
            <li>Requires a special dual stack ISATAP router to perform tunneling 
			and dual stack or IPv6-only clients. Dual stack routers and hosts 
			perform tunneling when communicating on the IPv4 network.</li>
            <li>Does not work through NAT.</li>
            <li>Automatically generates link-local addresses that includes the 
			IPv4 address of each host.
              <ul>
                <li>The prefix is the well-known link-local prefix: FE80::/16.</li>
                <li>The remaining prefix values are set to 0.</li>
                <li>The first two quartets of the interface ID are set to 
				0000:5EFE.</li>
                <li>The remaining two quartets use the IPv4 address written in 
				either dotted decimal or hexadecimal notation.</li>
              </ul>
              <blockquote class="info">
                For example, a host with the IPv4 address 192.168.12.155 would 
				have the following IPv6 address when using ISATAP: 
				FE80::5EFE:C0A8:0C9B (also designated as 
				FE80::5EFE:192.168.12.155).
              </blockquote>
            </li>
          </ul>Use ISATAP to begin a transition to IPv6 within a site. You can 
			start by adding a single ISATAP router and configuring each host as 
			an ISATAP client.
        </td>
      </tr>
      <tr>
        <td class="content">Teredo Tunneling</td>
        <td class="content">
          Teredo tunneling establishes a tunnel between individual hosts so they 
			can communicate through a private or public IPv4 network. Teredo 
			tunneling:
          <ul>
            <li>Is configured between individual hosts.</li>
            <li>Uses dual stack hosts and performs&nbsp; IPv6 tunneling to send 
			on the IPv4 network.</li>
            <li>Works through NAT.</li>
          </ul>In Windows 7, the Teredo component is enabled but inactive by 
			default. In Windows 8, Teredo is enabled by default on work and home 
			network profiles. On Linux, the Miredo client software is used to 
			implement Teredo tunneling.
        </td>
      </tr>
    </tbody>
  </table>
</div>

## IPv6 Address Assignment

<div id="TextViewer-root" class="TextViewer-root">
  <p>You can configure an IPv6 address with any of the methods in the following 
	table.</p>
<h3 style="color:#F96302">IPv6 Configuration Methods</h3>

  <table border="1">
    <tbody><tr class="header">
      <td class="centered">Method</td>
      <td class="contentheader">Description</td>
    </tr>
    <tr>
      <td class="centered">Static Full Assignment</td>
      <td class="content">The entire 128-bit address and all other configuration 
		information is statically assigned to the host.</td>
    </tr>
    <tr>
      <td class="centered">Static Partial Assignment</td>
      <td class="content">The prefix is statically assigned. The interface ID is 
		derived from the MAC address.</td>
    </tr>
    <tr>
      <td class="centered">Stateless Autoconfiguration</td>
      <td class="content">
        Clients automatically generate the interface ID and learn the subnet 
		prefix and default gateway through the Neighbor Discovery Protocol 
		(NDP). NDP uses the following messages for autoconfiguration:
        <ul>
          <li>A <i>Router solicitation</i> (RS) is a message the client sends to 
			request router response. </li>
          <li>A <i>Router advertisement</i> (RA) is a message the router sends 
			at two times: in response to RS messages and to inform clients of 
			the IPv6 subnet prefix and default gateway address.</li>
        </ul>Hosts also use NDP to discover the addresses of other interfaces on 
		the network, removing the need for the Address Resolution Protocol 
		(ARP).
        <blockquote class="info">
          NDP provides enough information for to address the client and for 
			clients to learn the addresses of other clients on the network. 
			However, it does not provide the client with DNS server information 
			or any other IP configuration information besides the IP address and 
			the default gateway.
        </blockquote>
      </td>
    </tr>
    <tr>
      <td class="centered">DHCPv6</td>
      <td class="content">
        IPv6 uses an updated version of DHCP, DHCPv6. It operates in one of two 
		modes:
        <ul>
          <li><i>Stateful</i> DHCPv6 is when the DHCP server provides each 
			client an IP address, default gateway, and other IP configuration 
			information (such as the DNS server IP address). The DHCP server 
			tracks the status (or state) of the client.</li>
          <li><i>Stateless</i> DHCPv6 does not provide the client an IP address 
			or track the status of each client. It supplies the client with the 
			DNS server IP address. Stateless DHCPv6 is most useful when used in 
			conjunction with stateless autoconfiguration.</li>
        </ul>
      </td>
    </tr>
  </tbody></table>

 <h3 style="color:#F96302">IPv6 Configuration Process</h3>
<p>When a host starts up, it uses the following process to configure the IPv6 
address for each interface:</p>

  <ol>
    <li>The host generates an IPv6 address using the link-local prefix 
	(FE80::/10) and modifies the MAC address to get the interface ID. For 
	example, if the MAC address is 20-0C-FB-BC-A0-07, the link-local address for 
	the interface is FE80::220C:FBFF:FEBC:A007.</li>
    <li>The host sends a neighbor solicitation (NS) message addressed to its own 
	link-local address to see if the address it has chosen is already in use:
      <ul>
        <li>If the address is in use, the other network host responds with a 
		neighbor advertisement (NA) message. The process stops, and you must 
		configure the host manually. </li>
        <li>If the address is not in use (no NA message is received), the 
		process continues.</li>
      </ul>
    </li>
    <li>The host waits for an RA message from a router to learn the prefix:
      <ul>
        <li>If an RA message is not received, the host uses the multicast 
		address FF02::2 to send an RS message addressed to all routers on the 
		subnet.</li>
        <li>The router sends an RA message addressed to all interfaces on the 
		subnet using the multicast address FF02::1.</li>
        <li>If no routers respond, the host attempts to use stateful DHCPv6 to 
		receive configuration information.</li>
      </ul>
    </li>
    <li>The RA message contains information that identifies how the IPv6 address 
	and other information should be configured. The following table shows 
	possible combinations:
      <table border="1">
        <tbody>
          <tr class="header">
            <td class="centered">Configuration Method</td>
            <td class="contentheader">Description</td>
          </tr>
          <tr>
            <td class="centered">Stateful Autoconfiguration</td>
            <td class="content">
              Obtains the interface ID, subnet prefix, default gateway, and 
				other configuration information from a DHCPv6 server.<br>
              <blockquote class="info">
                The host sends a REQUEST message addressed to the multicast 
				address FF02::1:2, requesting this information from the DHCPv6 
				server.
              </blockquote>
            </td>
          </tr>
          <tr>
            <td class="centered">Stateless Autoconfiguration</td>
            <td class="content">
              Sets the interface ID automatically.<br>
              Obtains the subnet prefix and default gateway from the RA message.<br>
              Obtains DNS and other configuration information from a DHCPv6 
				server.<br>
              <blockquote class="info">
                The host sends out an INFORMATION-REQUEST message addressed to 
				the multicast address FF02::1:2, requesting this information 
				from the DHCPv6 server.
              </blockquote>
            </td>
          </tr>
        </tbody>
      </table>
    </li>
    <li>If a manual address or stateful autoconfiguration is used, the host 
	sends an NS message to make sure the address is not already in use. If 
	stateless autoconfiguration is used, the NS message is unnecessary because 
	the interface ID was verified in step 2.</li>
  </ol>

  <h3 style="color:#F96302">IPv6 Address Management</h3>

  <p>A good way to manage IP addresses is to use IP address management (IPAM). 
	IPAM allows you to plan, track, and manage IP addresses using integrated 
	DHCP and DNS information. This allows administrators to keep a pool of 
	assignable IP addresses up-to-date. IPAM tools are becoming more important 
	for managing IPv6 networks because IPv6 networks have larger address pools, 
	different subnetting techniques, and more complex 128-bit hexadecimal 
	numbers.</p>
  <p>IPAM can manage the following information:</p>
  <ul>
    <li>IP addresses in use</li>
    <li>The user an IP address is assigned to</li>
    <li>Free IP address space</li>
    <li>The size of subnets, who uses them, and how many subnets are in use</li>
    <li>IP address status (permanent vs. temporary)</li>
    <li>Default routers that the various network devices use</li>
    <li>The host name associated with each IP address</li>
    <li>The hardware associated with each IP address</li>
  </ul>
</div>

## Multicast

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>How does multicast differ from unicast and broadcast?</li>
      <li>What is the IP address range reserved for multicast groups?</li>
      <li>What does a regular switch do when it receives a multicast frame?</li>
      <li>Which device would you configure to prevent multicast traffic from being sent to non-group members?</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Unicast</td>
      <td class="content">Messages are sent to a specific host address. The sending device must know the IP address of all
      recipients and must create a separate packet for each destination device.</td>
    </tr>
    <tr>
      <td class="centered">Broadcast</td>
      <td class="content">A single packet that, when sent, is processed by all 
		hosts. Broadcast packets are not typically forwarded by routers, so 
		broadcast traffic is limited to within a single subnet.</td>
    </tr>
    <tr>
      <td class="centered">IGMP</td>
      <td class="content">The Internet Group Management Protocol (IGMP) is used to identify group members and to forward multicast
      packets on to the segments where group members reside.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>Multicasting creates logical groups of hosts—messages sent to the group are 
	received by all group members. Multicasting is typically used for streaming 
	video and audio applications, such as video conferencing.</p>

  <p>Without multicasting, messages sent to a specific group only use the 
	following:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Method</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Unicast</td>
        <td class="content">Messages are sent to a specific host address. The 
		sending device must know the IP address of all recipients, and must 
		create a separate packet for each destination device.</td>
      </tr>
      <tr>
        <td class="centered">Broadcast</td>
        <td class="content">A single packet is sent to the broadcast address and 
		is processed by all hosts. All hosts, and not just group members, 
		receive the packet. Broadcast packets are not typically forwarded by 
		routers, so broadcast traffic is limited to within a single subnet.</td>
      </tr>
    </tbody>
  </table>

  <h3 style="color: #F96302">IGMP</h3>
  
  <p>The Internet Group Management Protocol (IGMP) is used to identify group 
	members and to forward multicast packets on to the segments where group 
	members reside. IGMP routers keep track of the attached subnets that have 
	group members, using the following process:</p>

  <ol>
    <li>A router sends out a host membership query. This query is addressed to 
	the IP address 224.0.0.1.
      <ul>
        <li>The address 224.0.0.1 is never assigned to a group because it is 
		used for the query messages sent by routers.</li>
      </ul>
    </li>
    <li>Hosts that are members of any groups respond with a list of the groups 
	they belong to. Each group is identified with a multicast IP address in the 
	range of 224.0.0.0 to 239.255.255.255.</li>
    <li>The router uses these responses to compile a list of the groups on the 
	subnet that have group members. Routers do not keep track of individual 
	hosts that are members of a group; they simply compile a list of groups on 
	the subnet that have at least one member.</li>
    <li>When a host joins a new group, it automatically sends a join group 
	message to the router. When the last host in a group leaves the group, it 
	sends a leave group message to the router.</li>
	<li>The IGMP router reports to upstream routers that they have members of a 
	specific group.
	<ul>
		<li>Upstream routers are the routers that exist between the router and 
		the server that sends out the multicast data stream. They keep track of 
		downstream routers that have group members.</li>
	</ul></li>
  </ol>

  <h3 style="color: #F96302">Multicast Stream</h3>
  
  <p>The following process is used when sending a multicast stream:</p>

  <ol>
    <li>The sending server sends packets addressed to the multicast group.</li>
    <li>Routers receive the multicast packets and check their lists of group 
	members.
      <ul>
        <li>If the router is connected to a subnet that has group members, or if 
		the subnet includes a downstream router with group members, the 
		multicast packet is sent on that subnet.</li>
        <li>If a subnet does not have any group members, the packet is not 
		forwarded on that subnet.</li>
        <li>If a router does not have any subnets with group members, the packet 
		is dropped and not forwarded.</li>
      </ul>
    </li>
    <li>Each intermediary router performs the same tasks until the data stream 
	eventually reaches the multicast client.</li>
  </ol>

  <h3 style="color: #F96302">Additional Facts</h3>
  
  <p>Additional multicasting facts include:</p>

  <ul>
    <li>Frames that contain multicast traffic are sent to a special MAC address. 
	The MAC address begins with 01-00-5E, with the last portion being a form of 
	the IP multicast group address. A single multicast MAC address could be 
	shared by up to 5 other IP multicast addresses.</li>
    <li>A regular switch that receives multicast traffic sends the traffic out 
	all ports, because the destination MAC address will be an unknown address. 
	This means that a host might see multicast traffic on its segment, even if 
	it isn't a member of the group. However, hosts that are not members of the 
	group will not process the frame because they will not associate the 
	multicast MAC address with their own address.</li>
    <li>IGMP snooping on a switch allows the switch to control which ports get 
	IGMP traffic for a specific group. With IGMP snooping, the switch identifies 
	which ports include members of a specific multicast group. When a message is 
	received for a group, the message is sent only to the ports that have a 
	group member connected.</li>
  </ul>
</div>

## Troubleshooting IP Configuration Issues

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>What does the <b>/release</b> switch do when used with <b>ipconfig</b>?</li>
      <li>How can you tell if a rogue DHCP server is active on your network?</li>
      <li>How do you know if a host is using APIPA?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Find information about IP configuration settings on Windows and Linux systems.</li>
      <li>Troubleshoot IP configuration problems.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">APIPA</td>
      <td class="content">APIPA (Automatic Private IP Addressing) is the Windows function that provides DHCP autoconfiguration
      addressing. When the DHCP process fails, Windows will automatically assign an IP address from the private range of
      169.254.0.1 to 169.254.255.254. Once the address has been assigned, the host uses Address Resolution Protocol (ARP) to verify
      that the chosen APIPA address is unique.</td>
    </tr>
    <tr>
      <td class="centered">ipconfig</td>
      <td class="content">ipconfig is a command line tool used to control the network connections on Windows machines.</td>
    </tr>
    <tr>
      <td class="centered">DHCP</td>
      <td class="content">Dynamic Host Configuration Protocol (DHCP) is a protocol used to centrally manage the distribution of IP
      addresses within a network.</td>
    </tr>
    <tr>
      <td class="centered">DNS</td>
      <td class="content">DNS stands for Domain Name System. The main function of DNS is to translate domain names into IP
      Addresses, which computers can understand.</td>
    </tr>
  </tbody></table>

  <p>This section helps you prepare for the following certification exam objectives:</p>

  <table class="objectives" border="1">
    <tbody><tr class="header">
      <td class="centered" width="260">Exam</td>
      <td class="contentheader">Objective</td>
    </tr>
    <tr>
      <td class="centered" width="260">TestOut Network Pro</td>
      <td class="content">
        <p>3.4 Use network tools to discover network devices and resources.</p>
        <p>5.2 Troubleshoot IP configuration issues to establish network communication.</p>
      </td>
    </tr>
    <tr>
      <td class="centered">CompTIA Network+</td>
      <td class="content">
        <div class="discussion">
          5.2 Given a scenario, use the appropriate tool.
          <ul>
            <li>Software tools
              <ul>
                <li>Command line</li>
                <li>ipconfig</li>
                <li>ifconfig</li>
              </ul>
            </li>
          </ul>
          <p>5.5 Given a scenario, troubleshoot common network service issues.</p>
          <ul>
            <li>Incorrect gateway</li>
            <li>Incorrect netmask</li>
            <li>Duplicate IP addresses</li>
            <li>Duplicate MAC addresses</li>
            <li>Expired IP address</li>
            <li>Exhausted DHCP scope</li>
            <li>Rogue DHCP server</li>
          </ul>
        </div>
      </td>
    </tr>
  </tbody></table>
</div>

## IPconfig Utility

<div id="TextViewer-root" class="TextViewer-root">
  <p>You can use <b>ipconfig /all</b> to troubleshoot IP configuration problems. The following table describes how the output for
  this command changes, based on how IP settings are configured and for specific problem situations:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Condition</td>
        <td class="content">ipconfig /all Output</td>
      </tr>
      <tr>
        <td class="centered">Static IP Configuration</td>
        <td class="content">
          If the workstation is configured with static IP information, the following conditions will exist:
          <ul>
            <li>The DHCP Enabled line will show No.</li>
            <li>The DHCP Server line will not be shown.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">DHCP Configuration</td>
        <td class="content">
          If the workstation has received configuration information from a DHCP server, the following conditions will exist:
          <ul>
            <li>The DHCP Enabled line will show Yes.</li>
            <li>The DHCP Server line will show the IP address of the DHCP server that sent the configuration information.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Rogue DHCP Server</td>
        <td class="content">
          A <i>rogue DHCP server</i> is an unauthorized DHCP server on the network. Symptoms of a rogue DHCP server include:
          <ul>
            <li>Conflicting IP addresses on the network</li>
            <li>Duplicate IP addresses on the network</li>
            <li>Incorrect IP configuration information on some hosts</li>
          </ul>To identify a rogue DHCP server using <b>ipconfig</b>, verify the DHCP server address. If this address is not the
          address of your DHCP server, you have a rogue DHCP server.
          <blockquote class="info">
            When you have a rogue DHCP server on the network, some hosts will likely receive configuration information from the
            correct DHCP server and others from the rogue DHCP server.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Incorrectly Configured DHCP Server</td>
        <td class="content">Your DHCP server can send out various IP configuration values, like the IP address and mask. If network
        hosts are configured with incorrect IP values (such as incorrect default gateway or DNS server addresses), first verify
        that the workstations are contacting the correct DHCP server. If the correct server is being used, go to the DHCP server to
        verify that it is sending out correct configuration information.</td>
      </tr>
      <tr>
        <td class="centered" height="273">APIPA Configuration</td>
        <td class="content">
          If the workstation used APIPA to set configuration information, the following conditions will exist:
          <ul>
            <li>The DHCP Enabled line will show Yes.</li>
            <li>The DHCP Server line will not be shown.</li>
            <li>The IP address will be in the range of 169.254.0.1 to 169.254.255.254, with a mask of 255.255.0.0.</li>
            <li>The Default Gateway line will be blank.</li>
            <li>The DNS Servers line will not include any IPv4 addresses.</li>
          </ul>
          <p>When APIPA is used, the workstation sets its own IP address and mask. It does not automatically configure default
          gateway or DNS server values. When APIPA is being used:</p>
          <ul>
            <li>Communication is restricted to hosts within the same subnet (there is no default gateway set).</li>
            <li>Hosts can communicate with other hosts that have used APIPA. If some hosts are still using an address assigned by
            the DHCP server (even if the DHCP server is down), those hosts will not be able to communicate with the APIPA
            hosts.</li>
            <li>Name resolution will not be performed (there are no DNS server addresses configured).</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Alternate Configuration</td>
        <td class="content">
          If the workstation has been configured using an alternate configuration, the following conditions will exist:
          <ul>
            <li>The DHCP Enabled line will show Yes.</li>
            <li>The DHCP Server line will not be shown.</li>
            <li>The IP address and subnet mask will be values other than the APIPA values.</li>
            <li>Default gateway and DNS server addresses will be configured using the alternate configuration values.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Duplicate MAC Addresses</td>
        <td class="content">
          The MAC address is a 12-digit hexadecimal number (48 bits). This address is unique, so you should not have duplicate
          addresses on your network. However, it is possible for two hosts to have the same MAC address, due to spoofing, a mistake
          during manufacturing, or if users choose a self-assigned address instead of the vendor-assigned hardware address. This
          last one is more common when using main frame systems that communicate via MAC addresses rather than protocol addresses
          (IP addresses).
          <p>An Ethernet switch keeps a table of which MAC addresses are attached to which ports. It uses the source address of
          frames it receives during the normal operation of the network to make the table. When the switch receives a frame, the
          source MAC is read and compared with the current table, and then added alongside whichever switch port it was received
          on. Therefore, if there are two hosts with the same MAC address, then the switch will update it's MAC table every
          time it receives a frame from either host. Reaching either host will be inconsistent and cause other problems as
          well.</p>
        </td>
      </tr>
    </tbody>
  </table>

  <p>Exhausted DHCP scope means that all of the addresses within the DHCP scope were depleted. As a consequence, a legitimate user
  is denied an IP address requested through DHCP and is not able to access the network. This situation is usually caused by an
  attack called DHCP starvation. This attack might be a DoS mechanism or be used together with a malicious rogue server attack to
  redirect traffic to a malicious computer ready to intercept traffic.</p>

  <p>If the workstation has received configuration information from the wrong DHCP server or has configured itself using APIPA, you
  may need to contact the DHCP server again once the DHCP problems have been resolved. Use the following commands:</p>

  <ul>
    <li><b>ipconfig /release</b> to stop using the current dynamic IP configuration parameters.</li>
    <li><b>ipconfig /renew</b> to retry the DHCP server request process to obtain IP configuration parameters.</li>
  </ul>

  <blockquote class="info">
    To display the TCP/IP configuration on a Linux computer, use the <b>ifconfig</b> command.
  </blockquote>
</div>

## Troubleshoot IP Communication

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>What is the difference between netstat and arp?</li>
      <li>If a ping test fails, what should you do?</li>
      <li>What information does tracert provide?</li>
      <li>What does TCPdump do?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Use ping and tracert.</li>
      <li>Use arp and netstat.</li>
      <li>Use tcpdump.</li>
      <li>Explore network communications.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">ping</td>
      <td class="content">ping sends an ICMP echo request/reply packet to a 
		remote host. A response from the remote host indicates that both hosts 
		are correctly configured and a connection exists between them. </td>
    </tr>
    <tr>
      <td class="centered">Address Resolution Protocol<br>
      (ARP)</td>
      <td class="content">Hosts use ARP to discover the MAC address of a device from its IP address.</td>
    </tr>
    <tr>
      <td class="centered">tcpdump</td>
      <td class="content">tcpdump is a packet analyzer that runs in a command 
		line utility. It allows the user to view TCP/IP and other packets as 
		they are transmitted and received over a computer's network.</td>
    </tr>
  </tbody></table>

  <p>This section helps you prepare for the following certification exam objectives:</p>

  <table class="objectives" border="1">
    <tbody><tr class="header">
      <td class="centered" width="260">Exam</td>
      <td class="contentheader">Objective</td>
    </tr>
    <tr>
      <td class="centered" width="260">TestOut Network Pro</td>
      <td class="content">
        <p>3.4 Use network tools to discover network devices and resources.</p>
        <p>5.2 Troubleshoot IP configuration issues to establish network communication.</p>
      </td>
    </tr>
    <tr>
      <td class="centered">CompTIA Network+</td>
      <td class="content">
        <p>1.3 Explain the concepts and characteristics of routing and switching.</p>
        <ul>
          <li>Segmentation and interface properties
            <ul>
              <li>ARP table</li>
            </ul>
          </li>
        </ul>
        <p>5.2 Given a scenario, use the appropriate tool.</p>
        <ul>
          <li>Software tools
            <ul>
              <li>Command line
                <ul>
                  <li>ping</li>
                  <li>tracert, traceroute</li>
                  <li>iptables</li>
                  <li>netstat</li>
                  <li>tcpdump</li>
                  <li>route</li>
                  <li>arp</li>
                </ul>
              </li>
            </ul>
          </li>
        </ul>
        <p>5.5 Given a scenario, troubleshoot common network service issues.</p>
        <ul>
          <li>Unresponsive service</li>
        </ul>
      </td>
    </tr>
  </tbody></table>
</div>
<br/>
<div id="TextViewer-root" class="TextViewer-root">
  <p>As part of the troubleshooting process, you need to identify the scope of the problem so you can take the proper actions to
  correct the problem.</p>

  <p>In this scenario, Workstation A can't communicate with Workstation C.</p>

  <p><img src="https://cdn.testout.com/_version_5012/netpro2018v5-en-us/en-us/resources/text/trb_comm/pingtest.jpg" width="565" height="273" border="0"></p>

<h3 style="color:#F96302">Troubleshooting Process</h3>

<p>The following table lists several tasks you can perform to troubleshoot the 
reported connectivity problem. These steps trace the problem backward from the 
remote host to the local host.
  Depending on the situation, you might be able to troubleshoot the problem more efficiently by skipping some tests or changing the
  order in which you perform them (you might even complete them in reverse 
order).</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Task</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Ping Host C</td>
        <td class="content">
          Often, the best way to start troubleshooting a problem is to ping the host you are trying to contact. This verifies the
          reported problem. If the ping is successful, the problem is not related to network connectivity. Check other problems,
          such as name resolution or service access.
          <blockquote class="info">
            If you have access to another computer, try pinging the destination host from that computer. If the ping is successful,
            skip the remaining tasks and troubleshoot the local host configuration or physical connection.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Ping Host D</td>
        <td class="content">If you cannot contact a specific remote host, try pinging another host in the same remote network. If
        the ping is successful, then the problem is with the remote host (for 
		example, a misconfiguration, broken link, or unavailable
        host).</td>
      </tr>
      <tr>
        <td class="centered">Ping Host E</td>
        <td class="content">If you cannot contact any host in the remote network, try pinging hosts on other remote networks (you
        might try several other networks). If the pings are successful or if you can contact some remote networks and not others,
        then the problem is with the routing path between your network and the specific remote network. Use the
        <b>traceroute</b>/<b>tracert</b> commands to check the path to the problem network.</td>
      </tr>
      <tr>
        <td class="centered">Ping the Default Gateway</td>
        <td class="content">If you cannot contact any remote network, ping the default gateway router. If the ping is successful but you still cannot contact any remote host, have the router administrator verify the router configuration. Check for
        broken links to the remote network, interfaces that have been shut down, and access control lists or other controls that
        might be blocking traffic.</td>
      </tr>
      <tr>
        <td class="centered">Ping Host B</td>
        <td class="content">If you cannot contact the default gateway router, ping other hosts on the local network. If the pings
        are successful, check the default gateway router.</td>
      </tr>
      <tr>
        <td class="centered">Troubleshoot the Local Host Connection or Configuration</td>
        <td class="content">
          If you cannot communicate with any host on the local network, then the problem is likely with the local host or its
          connection to the network. Troubleshoot by doing the following:
          <ul>
            <li>Check physical connectivity</li>
            <li>Validate the TCP/IP configuration on the local host</li>
            <li>Validate IP configuration settings</li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
  <blockquote class="info">
    You can use the route command on the router to view directly connected routes that have been set up. You can also use it on the
    default gateway of the local subnet and verify that the router has a route to the remote subnet. Another use of the route
    command is to view the routing table; this helps you see what networks the router knows about. In addition, the route command
    can be used to display additional networking information (not provided by ifconfig).
  </blockquote>
  <p>One special ping test you can perform is pinging the local host. By doing this, you are verifying that TCP/IP is correctly
  installed and configured on the local host. In essence, you are finding out if the workstation can communicate with itself. To
  ping the local host, use the following command:</p>
  <blockquote>
    <b>ping 127.0.0.1</b>
  </blockquote>
  <p>If this test fails, check to make sure TCP/IP is correctly configured on the system.</p>
  <blockquote class="info">
    This test does not check physical connectivity. The ping can succeed even if the host is disconnected from the network.
  </blockquote>
</div>

## ARP and netstat

<div id="TextViewer-root" class="TextViewer-root">
  <p>The following table lists several commands that you can use on a Windows 
	system to gather information about network connections.</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Tool</td>
        <td class="contentheader">Option(s)</td>
      </tr>
      <tr>
        <td class="centered"><b>arp</b></td>
        <td class="content"><b><a class="TextViewer-popupLink" onclick="popupHtml(0)">arp -a</a></b> shows the IP address-to-MAC address mapping table
        (the address cache).</td>
      </tr>
      <tr>
        <td rowspan="4" class="centered"><b>netstat</b></td>
        <td class="content"><b><a class="TextViewer-popupLink" onclick="popupHtml(1)">netstat</a></b> shows the active connections.</td>
      </tr>
      <tr>
        <td class="content"><b><a class="TextViewer-popupLink" onclick="popupHtml(2)">netstat -a</a></b> shows detailed information for active
        connections.</td>
      </tr>
      <tr>
        <td class="content"><b><a class="TextViewer-popupLink" onclick="popupHtml(3)">netstat -r</a></b> or <b>route print</b> shows the routing
        table of the local host.</td>
      </tr>
      <tr>
        <td class="content"><b><a class="TextViewer-popupLink" onclick="popupHtml(4)">netstat -s</a></b> shows TCP/IP statistics.</td>
      </tr>
      <tr>
        <td class="centered"><b>arp table</b></td>
        <td class="content"><b><a class="TextViewer-popupLink" onclick="popupHtml(5)">arp tables</a></b> allow a system to build frames targeting
        remote MAC addresses.</td>
      </tr>
    </tbody>
  </table>
  <blockquote class="info">
    Local computers have a cache of recently used IP addresses and their 
	corresponding MAC addresses. When a computer needs to contact another 
	computer on its own subnet, it first checks its cache for an entry of the IP 
	address. If the entry is found, the corresponding MAC address is used to 
	communicate with the destination computer. The cache can cause problems if 
	the MAC address for a computer has recently changed (for example, if the network interface card has been replaced). To correct a problem, use
    the <b>netsh</b> command to clear the ARP cache.
  </blockquote>
</div>
<br/>
  <p><b>arp -a</b> shows the IP address-to-MAC address mapping table (the address cache).</p>

  <p>A sample output looks like this:</p>

  <table border="1">
    <tbody>
      <tr>
        <td>

```Interface: 192.168.1.141 on Interface 0x1000003
  Internet Address      Physical Address      Type
  192.168.1.1           00-40-10-18-7c-ed     dynamic
  192.168.1.20          00-0e-0c-4e-e0-b2     dynamic
  192.168.1.21          00-0e-0c-4e-e1-fe     dynamic
  192.168.1.22          00-0e-0c-4e-df-c6     dynamic
  192.168.1.23          00-d0-b7-b7-c2-af     dynamic
  192.168.1.26          00-0e-0c-4e-e9-d6     dynamic
```


  </table>

  <p>Occasionally, the ARP table will have stale entries. This happens when:</p>

  <ul>
    <li>The IP address assigned to a host changes (for example, if a DHCP server assigns it a different IP address).</li>
    <li>The MAC address of a host changes (for example, if the NIC is replaced).</li>
  </ul>
  <p>If this is the case, when the local computer consults its cache for ARP information, the information will be incorrect, and the
  computer will be unable to contact the remote host. To correct the problem, use the <b>arp 
	-d *</b> command to delete the cache.
  This causes the computer to use ARP to rediscover the information.</p>
<br/>
  <p><b>netstat</b> shows the active connections.</p>

  <p>A sample output looks like this:</p>

```
Active Connections

  Proto  Local Address        Foreign Address                   State
  TCP    wrk1:microsoft-ds    wrk1.westsim.local:1342          ESTABLISHED
  TCP    wrk1:1342            wrk1.westsim.local:microsoft-ds  ESTABLISHED
  TCP    wrk1:1088            srv1.westsim.local:1026          ESTABLISHED
  TCP    wrk1:1096            srv1.westsim.local:1865          ESTABLISHED
  TCP    wrk1:1232            srv1.westsim.local:microsoft-ds  ESTABLISHED 
```



  <meta http-equiv="Content-type" content="text/html; charset=UTF-8">
  <link href="../../style2.css" rel="stylesheet" type="text/css">

  <title></title>



  <p><b>netstat -a</b> shows detailed information for active connections.</p>

  <p>A sample output looks like this:</p>

  <table>
    <tbody>
      <tr>
        <td>

```
Active Connections

  Proto  Local Address     Foreign Address                     State
  TCP    wrk1:epmap        wrk1.westsim.local:0                LISTENING
  TCP    wrk1:microsoft-ds wrk1.westsim.local:0                LISTENING
  TCP    wrk1:1039         wrk1.westsim.local:0                LISTENING
  TCP    wrk1:1083         wrk1.westsim.local:0                LISTENING
  TCP    wrk1:1088         wrk1.westsim.local:0                LISTENING 
  TCP    wrk1:1096         wrk1.westsim.local:0                LISTENING
  TCP    wrk1:1232         wrk1.westsim.local:0                LISTENING
  TCP    wrk1:netbios-ssn  wrk1.westsim.local:0                LISTENING
  TCP    wrk1:1088         srv1.westsim.local:1026             ESTABLISHED
  TCP    wrk1:1096         srv1.westsim.local:1865             ESTABLISHED
  TCP    wrk1:1232         srv1.westsim.local:microsoft-ds     ESTABLISHED
  UDP    wrk1:microsoft-ds *:*
  UDP    wrk1:1027         *:*
  UDP    wrk1:1044         *:*
  UDP    wrk1:1091         *:*
  UDP    wrk1:2967         *:*
  UDP    wrk1:1305         *:*
  UDP    wrk1:netbios-ns   *:*
  UDP    wrk1:netbios-dgm  *:*
  UDP    wrk1:isakmp       *:* 
```

  <p><b>netstat -r</b> or <b>route print</b> shows the routing table of the local host.</p>

  <p>A sample output looks like this:</p>

  <table>
    <tbody>
      <tr>
        <td>

```
Route Table
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x1000003 ...00 06 5b 1c 92 b8 ...... 3Com EtherLink PCI
===========================================================================
===========================================================================
Active Routes:
Network Destination       Netmask            Gateway      Interface  Metric
          0.0.0.0         0.0.0.0        192.168.1.1  192.168.1.141       1
        127.0.0.0       255.0.0.0          127.0.0.1      127.0.0.1       1
      192.168.1.0   255.255.255.0      192.168.1.141  192.168.1.141       1
    192.168.1.141 255.255.255.255          127.0.0.1      127.0.0.1       1
    192.168.1.255 255.255.255.255      192.168.1.141  192.168.1.141       1
        224.0.0.0       224.0.0.0      192.168.1.141  192.168.1.141       1
  255.255.255.255 255.255.255.255      192.168.1.141  192.168.1.141       1
Default Gateway:      192.168.1.1
===========================================================================
Persistent Routes:
  None
```



  <link href="../../../style2.css" rel="stylesheet" type="text/css">

  <title></title>



  <p><b>netstat -s</b> shows TCP/IP statistics.</p>

  <p>A sample output looks like this:</p>

```
IP Statistics

  Packets Received                  = 81978
  Received Header Errors            = 0
  Received Address Errors           = 374 
  Datagrams Forwarded               = 0
  Unknown Protocols Received        = 0
  Received Packets Discarded        = 0
  Received Packets Delivered        = 81776
  Output Requests                   = 63048 
  Routing Discards                  = 0
  Discarded Output Packets          = 0
  Output Packet No Route            = 0
  Reassembly Required               = 0
  Reassembly Successful             = 0
  Reassembly Failures               = 0
  Datagrams Successfully Fragmented = 0
  Datagrams Failing Fragmentation   = 0 
  Fragments Created                 = 0

ICMP Statistics

                            Received    Sent
  Messages                  52          56
  Errors                    0           0
  Destination Unreachable   3           0
  Time Exceeded             0           0
  Parameter Problems        0           0
  Source Quenches           0           0
  Redirects                 0           0
  Echos                     0           56
  Echo Replies              49          0
  Timestamps                0           0
  Timestamp Replies         0           0
  Address Masks             0           0
  Address Mask Replies      0           0

TCP Statistics

  Active Opens                       = 225
  Passive Opens                      = 17
  Failed Connection Attempts         = 2
  Reset Connections                  = 26
  Current Connections                = 3
  Segments Received                  = 77862
  Segments Sent                      = 62130
  Segments Retransmitted             = 0

UDP Statistics

  Datagrams Received                 = 3223
  No Ports                           = 691
  Receive Errors                     = 0
  Datagrams Sent                     = 862 
```



  <meta http-equiv="Content-type" content="text/html; charset=UTF-8">
  <link href="../../style2.css" rel="stylesheet" type="text/css">

  <title></title>



  <p><b>arp -a</b> shows the IP address-to-MAC address mapping table (the address cache).</p>

  <p>A sample output looks like this:</p>

```
Interface: 192.168.1.141 on Interface 0x1000003
  Internet Address      Physical Address      Type
  192.168.1.1           00-40-10-18-7c-ed     dynamic
  192.168.1.20          00-0e-0c-4e-e0-b2     dynamic
  192.168.1.21          00-0e-0c-4e-e1-fe     dynamic
  192.168.1.22          00-0e-0c-4e-df-c6     dynamic
  192.168.1.23          00-d0-b7-b7-c2-af     dynamic
  192.168.1.26          00-0e-0c-4e-e9-d6     dynamic
```

  <p>Occasionally, the ARP table will have stale entries. This happens when:</p>
  <ul>
    <li>The IP address assigned to a host changes (for example, if a DHCP server assigns it a different IP address).</li>
    <li>The MAC address of a host changes (for example, if the NIC is replaced).</li>
  </ul>
  <p>If this is the case, when the local computer consults its cache for ARP information, the information will be incorrect, and the
  computer will be unable to contact the remote host. To correct the problem, use the <b>arp 
	-d *</b> command to delete the cache.
  This causes the computer to use ARP to rediscover the information.</p>

## tcpdump 

<div id="TextViewer-root" class="TextViewer-root">
  <p>TCPdump is a packet analyzer that runs in a command line utility. It allows the user to view TCP/IP and other packets as they
  are transmitted and received over on a computer's network. In this lesson, you will learn about:</p>

  <ul>
    <li>Common uses</li>
    <li>Options</li>
    <li>Expression examples</li>
  </ul>

  <h3 style="color:#F96302">Common Uses</h3>

  <p>TCPdump prints the contents of network packets. It can read packets from a network interface card or a previously captured
  packet file. TCPdump can write packets to standard output or a file.</p>

  <p>You can TCPdump to intercept and display the network traffic of another user or computer, including user credentials, the
  content of packets, and other unencrypted information.</p>

  <h3 style="color: #F96302">Options</h3>

  <p>These are some of the many configuration options for TCPdump. For a complete list of options refer to the TCPdump MAN (manual)
  page.</p>

  <table border="1">
    <tbody><tr class="header">
      <td class="centered">Option</td>
      <td class="contentheader">Description</td>
    </tr>
    <tr>
      <td class="centered">-i any</td>
      <td class="content">Listen on all interfaces to check for traffic traffic.</td>
    </tr>
    <tr>
      <td class="centered">-i eth0</td>
      <td class="content">Listen on the eth0 interface.</td>
    </tr>
    <tr>
      <td class="centered">-D</td>
      <td class="content">Show the list of available interfaces.</td>
    </tr>
    <tr>
      <td class="centered">-n</td>
      <td class="content">Don't resolve host names.</td>
    </tr>
    <tr>
      <td class="centered">-nn</td>
      <td class="content">Don't resolve host names or port names.</td>
    </tr>
    <tr>
      <td class="centered">-q</td>
      <td class="content">Be less verbose (more quiet) with your output.</td>
    </tr>
    <tr>
      <td class="centered">-t</td>
      <td class="content">Create a timestamp output humans can read.</td>
    </tr>
    <tr>
      <td class="centered">-tttt</td>
      <td class="content">Create a timestamp output that's maximally readable for humans.</td>
    </tr>
    <tr>
      <td class="centered">-X</td>
      <td class="content">Show the packet's contents in both hex and ASCII.</td>
    </tr>
    <tr>
      <td class="centered">-XX</td>
      <td class="content">Same as -X, but also shows the Ethernet header.</td>
    </tr>
    <tr>
      <td class="centered">-v, -vv, -vvv</td>
      <td class="content">Increase the amount of packet information you get back.</td>
    </tr>
    <tr>
      <td class="centered">-c</td>
      <td class="content">Only receive a certain number of packets and then stop.</td>
    </tr>
    <tr>
      <td class="centered">-s</td>
      <td class="content">Define the snaplength (size) of the capture in bytes. Use -s0 to capture everything unless you are
      intentionally capturing less.</td>
    </tr>
    <tr>
      <td class="centered">-S</td>
      <td class="content">Print absolute sequence numbers.</td>
    </tr>
    <tr>
      <td class="centered">-e</td>
      <td class="content">Retrieve the Ethernet header.</td>
    </tr>
    <tr>
      <td class="centered">-q</td>
      <td class="content">Show less protocol information.</td>
    </tr>
    <tr>
      <td class="centered">-E</td>
      <td class="content">Decrypt IPsec traffic by providing an encryption key.</td>
    </tr>
  </tbody></table>

  <h3 style="color:#F96302">Expression Examples</h3>

  <p>Expressions allow you to filter traffic and find exactly what you need.<br>
  <br>
  There are three main types of expression: type, dir, and proto.</p>

  <ul>
    <li>The type options are host, net (the network address), and port.</li>
    <li>Direction lets you insert the src (source) and dst (destination) commands.</li>
    <li>Protocol lets you designate tcp, udp, icmp, ah, and many more options.</li>
  </ul>

  <p>Some examples of uses for TCPdump include the following:</p>

  <blockquote class="info">
    Commands are case sensitive.
  </blockquote>

  <table border="1">
    <tbody><tr class="header">
      <td class="contentheader">TCPdump Example</td>
      <td class="contentheader">Description</td>
    </tr>
    <tr>
      <td class="content">tcpdump -D</td>
      <td class="content">Display the list of interfaces TCPdump can listen to.</td>
    </tr>
    <tr>
      <td class="content">tcpdump -n host 192.168.0.1</td>
      <td class="content">Capture any packets that list 192.168.0.1 as the source or destination host. Displays IP addresses and
      port numbers.</td>
    </tr>
    <tr>
      <td class="content">tcpdump -i eth0</td>
      <td class="content">Listen on interface eth0.</td>
    </tr>
    <tr>
      <td class="content" height="39">tcpdump -i any</td>
      <td class="content" height="39">Listen on any available interface.</td>
    </tr>
    <tr>
      <td class="content">tcpdump -n dst net 192.168.0.0/24</td>
      <td class="content">Capture any packets that list 192.168.0.0/24 as the destination network. Displays IP addresses and port
      numbers.</td>
    </tr>
    <tr>
      <td class="content">tcpdump -n src net 192.168.1.0/24</td>
      <td class="content">Capture any packets that list 192.168.1.0/24 as the source network. Displays IP addresses and port
      numbers.</td>
    </tr>
    <tr>
      <td class="content">tcpdump -n dst port 23</td>
      <td class="content">Capture any packets that list 23 as the destination port. Displays IP addresses and port numbers.</td>
    </tr>
    <tr>
      <td class="content">tcpdump -n "dst host 192.168.1.1 and (dst port 80 or dst port 443)"</td>
      <td class="content">Capture any packets that list 192.168.0.1 as the destination IP and 80 or 443as the destination port.
      Displays IP addresses and port numbers.</td>
    </tr>
  </tbody></table>
</div>

## Troubleshooting Name Resolution

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>What are the symptoms of name resolution problems?</li>w
      <li>What is the difference between <b>nslookup</b> and <b>dig</b>?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Use nslookup</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">tracert or traceroute</td>
      <td class="content">The tracert or traceroute commands are used to show details about the path that a packet takes from the
      computer to whatever destination you specify.</td>
    </tr>
    <tr>
      <td class="centered">nslookup</td>
      <td class="content">A command-line tool used (in Windows and other operating systems) to query the Domain Name System (DNS)
      to obtain the domain name, the IP address mapping, or for any other specific DNS record.</td>
    </tr>
    <tr>
      <td class="centered">dig</td>
      <td class="content">Domain Information Groper (dig) is a Unix-like network 
		administration command-line tool used to
      determine what a particular DNS server thinks the given host’s IP address should be.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>Common name resolution problems include the following:</p>

  <ul>
    <li>The DNS server could be down or otherwise unreachable.</li>

    <li>There may be a routing problem between the sending host and the DNS 
	server.</li>

    <li>The sending host could be configured with the wrong IP address for the 
	DNS server.</li>
  </ul>

  <p>Name resolution problems typically have the following symptoms:</p>

  <ul>
    <li>You can ping a destination host using its IP address, but not its host 
	name.</li>

    <li>Applications that use hostnames fail. This could include:

      <ul>
        <li>Entering a URL into a browser.</li>

        <li>Pinging the host using the hostname.</li>

        <li>Searching for the host by its name.</li>
      </ul>
    </li>
  </ul>

  <p>To troubleshoot DNS name resolution, use the following tools:</p>

  <ul>
    <li><b>ping</b></li>
    <li><b>tracert</b> (Windows) or <b>traceroute</b> (Linux)</li>
    <li><b>nslookup</b></li>
    <li><b>dig</b> (Linux)</li>
    <li><b>host</b> (Linux)</li>
  </ul>

  <h3 style="color:#F96302">Troubleshoot DNS Name Resolution With Commands </h3>

  <p>The following table lists several ways to troubleshoot with commands:</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Command</td>
        <td class="contentheader">Purpose</td>
        <td class="contentheader">Example</td>
      </tr>
      <tr>
        <td class="centered"><b>ping</b></td>
        <td class="content">Contacts the DNS server to see if it responds. Be 
		aware that the firewall protecting the DNS server may be configured to 
		drop ICMP packets in order to prevent DoS attacks; if the server doesn't 
		respond, it is not necessarily down.</td>
        <td class="centered">
          <p class="code">ping 8.8.4.4</p>
        </td>
      </tr>
      <tr>
        <td class="centered"><b>tracert</b> or <b>traceroute</b></td>
        <td class="content">Tests the route between your workstation and the DNS 
		server.</td>
        <td class="centered">
          <p class="code">tracert 8.8.4.4</p>
        </td>
      </tr>
      <tr>
        <td class="centered"><b>nslookup</b> <i>[host]</i></td>
        <td class="content">Queries the IP address of a host.</td>
        <td class="centered">
          <p class="code">nslookup www.mit.edu</p>
        </td>
      </tr>
      <tr>
        <td class="centered"><b>nslookup</b></td>
        <td class="content">Starts <b>nslookup</b> in interactive mode. The 
		default interactive mode query is for A records, but you can use the <b>
		set type=</b> command to change the query type.</td>
        <td class="centered">
          <p class="code">nslookup set type=ns</p>
        </td>
      </tr>
      <tr>
        <td class="centered"><b>dig</b> <i>host name</i><br>
        <b>host</b> <i>host name</i></td>
        <td class="content">
          Queries a host. The default query is for A records. You can change the 
			default search by appending one of the record types below to the end 
			of the command:
          <ul>
            <li>a—address records</li>
            <li>any—any type of record</li>
            <li>mx—mail exchange records</li>
            <li>ns—name server records</li>
            <li>soa—sort of authority records</li>
            <li>hinfo—host info records</li>
            <li>axfr—all records in the zone</li>
            <li>txt—text records</li>
          </ul>
        </td>
        <td class="centered">
          <p class="code">dig www.vulture.com ns<br>
          host www.vulture.com -t ns</p>
        </td>
      </tr>
      <tr>
        <td class="centered"><b>dig</b> <i>@IP address or host name</i> <i>
		domain</i></td>
        <td class="content">Queries the root server at the IP address or host 
		name for the domain's A records. You can change the default query type 
		by appending a different record type to the end of the command.</td>
        <td class="centered">
          <p class="code">dig @192.168.1.1 vulture.com ns</p>
        </td>
      </tr>
      <tr>
        <td class="centered"><b>dig -x</b> <i>IP address</i><br>
        <b>host</b> <i>IP address</i></td>
        <td class="content">Finds the host name for the queried IP address.</td>
        <td class="centered">
          <p class="code"><b>dig -x 62.34.4.72</b><br>
          <b>host 62.34.4.72</b></p>
        </td>
      </tr>
    </tbody>
  </table>

  <blockquote class="info">
    Local computers have a cache of recently resolved DNS names. The cache holds 
	the DNS name and its IP address. When you use a DNS name, the computer first 
	checks its cache. If the name is in the cache, the corresponding IP address 
	is used. This can cause problems if a host's IP address has changed. Old 
	values in the cache might continue to be used temporarily, making 
	communication via the DNS name impossible. To correct this problem on a 
	Windows computer, run <b>ipconfig /flushdns</b> to delete the local DNS name 
	cache.
  </blockquote>
</div>

</br>

# Chapter 6 Switch Management
###### [Back to top](#Network-Security-and-Data-Communications)
<br/>

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>
  <div class="discussion">
    <ul>
      <li>What are the requirements for connecting a VTY (virtual terminal) to a Cisco device?</li>
      <li>What types of cable can you use to connect a PC to a router console port?</li>
      <li>What is the difference between a managed switch and an unmanaged switch?</li>
      <li>What is the difference between in-band and out-of-band management?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Use the command line interface (CLI).</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Managed Switch</td>
      <td class="content">A switch that must be configured before you can use 
		it.</td>
    </tr>
    <tr>
      <td class="centered">Unmanaged Switch</td>
      <td class="content">An unmanaged switch allows Ethernet devices to communicate with one another automatically using
      auto-negotiation to determine parameters such as the data rate and whether to use half-duplex or full-duplex mode.</td>
    </tr>
    <tr>
      <td class="centered">Out-of-Band Management</td>
      <td class="content">Out-of-band management allows you to use a dedicated communication channel that separates management
      traffic from normal network traffic. Network switches and routers allow you to use console redirection to access the
      device's console through a built-in serial or USB port.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>You must configure an enterprise network switch before you implement it. An <i>unmanaged switch</i> is a low-end switches
  available from many retail stores. To implement an unmanaged switch, plug it into a power outlet and connect your network devices
  with UTP cables. While unmanaged switches are convenient and easy to implement, they lack many of the advanced management and
  security features available. It is preferable to use a managed switch instead. A <i>managed switch</i> is a switch that must be configured before you
  can use it.</p>

  <h3 style="color:#F96302">In-Band Management</h3>

  <p>In-band management allows you to perform router and switch management tasks using a standard network connection. You do this
  with management utilities your workstation operating system provides through a network connection. For example, tools such as
  Telnet and SSH provide in-band management. Using the same network connection for both data and management has several
  drawbacks:</p>

  <ul>
    <li>You must compete with normal network traffic for bandwidth.</li>

    <li>The network traffic created by the management utilities must have protection from sniffing attacks to ensure that hackers
    cannot capture sensitive configuration information.</li>

    <li>If the network connection is unavailable or the device is unresponsive to network communications, you cannot perform
    management tasks.</li>
  </ul>

  <h3 style="color:#F96302">Out-of-Band Management</h3>

  <p>Out-of-band management allows you to use a dedicated communication channel 
	that separates management traffic from normal network traffic. Network switches and routers 
	allow you to use console redirection to access the device's console through a
  built-in serial or USB port. For example, Cisco routers and switches do not use monitors, and you cannot connect a keyboard or a
  mouse directly to the device. Instead, you connect a standard PC to the device's console port to manage the device.</p>

  <h3 style="color:#F96302">System Management</h3>

  <p>Use the following options to manage a Cisco device:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Cisco Connection Type</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Console</td>
        <td class="content">
          A console connection allows for a direct connection through a PC to the console port on the device. The PC needs a
          terminal emulation program (such as PuTTY) to connect to the device's command line interface. This is an example of
          out-of-band management. In the terminal emulation program, use the following settings:
          <ul>
            <li>9600 baud (or a rate supported by your router)</li>
            <li>Data bits = 8 (default)</li>
            <li>Parity = None (default)</li>
            <li>Stop bits = 1 (default)</li>
            <li>Flow control = None</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Virtual Terminal (VTY)</td>
        <td class="content">A VTY connection connects through a LAN or WAN interface configured on the device. Use a program (such
        as PuTTY) to open the command line interface. This is an example of in-band management. The Cisco device must be configured
        with an IP address before a VTY connection can be made.</td>
      </tr>
      <tr>
        <td class="centered">Security Device Manager (SDM)</td>
        <td class="content">
          The Cisco SDM allows a web browser connection to the device using HTTPS. When connected, the SDM allows you to manage
          the security features and network connections through a web-based graphical user interface. This is an example of in-band
          management. Be aware of the following SDM settings:
          <ul>
            <li>10.10.10.1 is the default IP address of the SDM.</li>
            <li>The default value for both the username and password is <b>cisco</b>.</li>
          </ul>
          <blockquote class="info">
            A new router may not be completely configured for an SDM connection, so you may need to make a console connection
            first.
          </blockquote>
        </td>
      </tr>
    </tbody>
  </table>

  <h3 style="color:#F96302">Router and Switch Connection</h3>

  <p>Use the following cable types to make the initial connection to the switch or router for device management:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Cable Type</td>
        <td class="centered">Pin-outs</td>
        <td class="contentheader">Use</td>
      </tr>
      <tr>
        <td class="centered"><img src="https://cdn.testout.com/_version_5012/netpro2018v5-en-us/en-us/resources/text/cab_typ/ro.jpg" width="320" height="180" border="0"><br>
        Rollover Ethernet Cable</td>
        <td class="centered">1 ' 8<br>
        2 ' 7<br>
        3 ' 6<br>
        4 ' 5<br>
        5 ' 4<br>
        6 ' 3<br>
        7 ' 2<br>
        8 ' 1</td>
        <td class="content">
          Use a rollover Ethernet cable to connect the device's console port to the serial port on a PC. Connect the RJ45 end
          to the console port, and connect the serial end to the PC. A rollover cable is also called a <i>console cable</i>.
          <blockquote class="info">
            Many recently developed Cisco devices use a USB for the console connector, so you can access it with any standard USB
            cable.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered"><img src="https://cdn.testout.com/_version_5012/netpro2018v5-en-us/en-us/resources/text/cab_typ/st.jpg" width="320" height="180" border="0"><br>
        Straight-Through Ethernet Cable</td>
        <td class="centered">1 ' 1<br>
        2 ' 2<br>
        3 ' 3<br>
        6 ' 6</td>
        <td class="content">
          Use a straight-through Ethernet cable to connect an Ethernet port on a router to an Ethernet port on a hub or switch. You
          can then access the router from another PC connected to the same network using a VTY connection.
          <blockquote class="info">
            If the router has an AUI port, connect one end to an AUI transceiver before you connect to the router.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered"><img src="https://cdn.testout.com/_version_5012/netpro2018v5-en-us/en-us/resources/text/cab_typ/co.jpg" width="320" height="180" border="0"><br>
        Crossover Ethernet Cable</td>
        <td class="centered">1 ' 3<br>
        2 ' 6<br>
        3 ' 1<br>
        6 ' 2</td>
        <td class="content">
          Use a crossover Ethernet cable to connect an Ethernet port on a router directly to the NIC in a PC. Establish a VTY
          session from the PC to connect to the device.
          <blockquote class="info">
            If the router has an AUI port, connect one end to an AUI transceiver before you connect to the router.
          </blockquote>
        </td>
      </tr>
    </tbody>
  </table>
</div>

## Switch IP Configuration

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>Why would you configure an IP address on a switch?</li>
      <li>What does the <b>ip address dhcp</b> command allow you to do?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure management VLAN settings.</li>
      <li>Configure switch IP settings.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">VLAN</td>
      <td class="content">A VLAN (Virtual Local Network) is a group of devices on one or more local area networks (LANs) that are
      configured to communicate as if they were attached to the same wire when, in fact, they could be located on a number of
      different LAN segments.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>Keep in mind the following facts about IP addresses configured on switches:</p>

  <ul>
    <li>Basic switches operate at Layer 2, so they are able to perform switching functions with no IP address configured.</li>
    <li>A switch does not need to have an IP address configured unless you want to manage it with an in-band management utility
    such as SSH or a web-based interface.</li>
    <li>Switch ports do not have IP addresses unless the switch performs Layer 3 switching, which is not supported on all
    switches.</li>
    <li>The switch itself only has one active IP address. The IP address identifies the switch as a host on the network.</li>
  </ul>

  <h3 style="color:#F96302">Configure the Switch IP Address</h3>

  <p>To configure the switch IP address, set the address on the VLAN interface (a logical interface defined on the switch to allow
  management functions). By default, the VLAN is VLAN 1. Use the following commands to configure the switch IP address:</p>

  <code>
    switch#config terminal<br>
    <br>
    switch(config)#interface vlan 1<br>
    <br>
    switch(config-if)#ip address <i>IP_address subnet_mask</i><br>
    <br>
    switch(config-if)#no shutdown
  </code>

  <h3 style="color:#F96302">Enable Management From a Remote Network</h3>

  <p>To enable management from a remote network, configure the default gateway. Use the following command in global configuration
  mode:</p>

  <code>
    switch(config)#ip default-gateway <i>IP_address</i>
  </code>

  <blockquote class="info">
    You can use the <code>ip address dhcp</code> command to configure a switch (or a router) to get its IP address from a DHCP server.
    The DHCP server can be configured to deliver the default gateway and DNS server addresses to the Cisco device as well. A
    manually configured default gateway address overrides any address received from the DHCP server.
  </blockquote>

  <blockquote class="info">
    You can use the <code>show cdp neighbors detail</code> command to displays detailed information about neighboring devices including
    network address, enabled protocols, hold time, and software version.
  </blockquote>
</div>

## Switch Interface Configuration

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>How does the VLAN interface configuration mode differ from Ethernet, FastEthernet, and GigabitEthernet interface
      configuration modes?</li>
      <li>What must you consider if you manually configure speed or duplex settings?</li>
      <li>What happens when autonegotiation fails for the Ethernet interface on a Cisco device?</li>
      <li>What is the default setting for all ports on a switch?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure switch interfaces.</li>
      <li>Configure switch ports.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Forwarding Database</td>
      <td class="content">A forwarding database is a list of Layer 2 MAC addresses and the ports used to reach each device.</td>
    </tr>
    <tr>
      <td class="centered">Content Addressable Memory<br>
      (CAM)</td>
      <td class="content">The Content Addressable Memory (CAM) table stores the relationship between the MAC addresses on the
      network and the switch port each one is connected to.</td>
    </tr>
  </tbody></table>
</div>

## Switch Forwarding

<div id="TextViewer-root" class="TextViewer-root">
  <p>Bridges and switches build forwarding databases. A <i>forwarding database</i> is a list of Layer 2 MAC addresses and the ports
  used to reach each device. Bridges and switches automatically learn about devices to build the forwarding database, but a network
  administrator can also program the device database manually. When a frame arrives on a switch port (also called an interface),
  the switch examines the source and destination address in the frame header and uses the information to complete the following
  tasks:</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Step</td>
        <td class="contentheader">Results</td>
      </tr>
      <tr>
        <td class="centered">
          <p>1. The switch examines the source MAC address of the frame and notes which switch port the frame arrived on.</p>
        </td>
        <td class="content">
          <p>If the source MAC address is:</p>
          <ul>
            <li>Not in the switch's Content Addressable Memory (CAM) table, a new entry is added to the table that maps the
            source device's MAC address to the port on which the frame was received. Over time, the switch builds a map of the
            devices that are connected to specific switch ports.</li>
            <li>Already mapped to the port on which the frame was received, no changes are made to the switch's CAM table.</li>
            <li>Already in the switch's CAM table but the frame was received on a different switch port, the switch updates the
            record in the CAM table with the new port.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">
          <p>2. The switch examines the destination MAC address of the frame.</p>
        </td>
        <td class="content">
          <p>If the destination MAC address of the frame is:</p>
          <ul>
            <li>A broadcast address, then the switch sends a copy of the frame to all connected devices on all ports. This is
            called flooding the frame.</li>
            <li>A unicast address but no mapping exists in the CAM table for the destination address, the switch floods the frame
            to all ports. The connected device that the frame is addressed to will accept and process the frame. All other devices
            will drop the frame.</li>
            <li>A unicast address and mapping exists in the CAM table for the destination address, the switch sends the frame to
            the switch port specified in the CAM table. This is called forwarding the frame.</li>
            <li>A unicast address and mapping exists in the CAM table for the destination address, but the destination device is
            connected to the same port from which the frame was received, the switch ignores the frame and does not forward it.
            This is called filtering the frame.</li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
</div>

## Switch Configuration Mode (Cisco)

<div id="TextViewer-root" class="TextViewer-root">
  <p>The following image illustrates some of the configuration modes available on a Cisco switch:</p>

  <p><img src="https://cdn.testout.com/_version_5012/netpro2018v5-en-us/en-us/resources/text/swi_mode/swi_mode.jpg" border="0"></p>

  <h3 style="color:#F96302">Cisco Switch Configuration Modes</h3>

  <p>The following table describes some of these configuration modes:</p>

  <table border="1">
    <tbody>
    <tr class="header">
      <td class="centered">Mode</td>
      <td class="contentheader">Details</td>
      <td class="contentheader" width="200">CLI Mode Prompt</td>
    </tr>
    <tr>
      <td class="centered">Interface Configuration</td>
      <td class="content">
        <p>The switch has multiple interface modes depending on the physical (or logical) interface type. For this course, you
        should be familiar with the following switch interface modes:</p>
        <ul>
          <li>Ethernet (10 Mbps Ethernet)</li>
          <li>FastEthernet (100 Mbps Ethernet)</li>
          <li>GigabitEthernet (1 GB Ethernet)</li>
          <li>VLAN</li>
        </ul>
        <blockquote class="info">
          The VLAN interface configuration mode is used to configure the switch IP address and for other management functions. It
          is a logical management interface configuration mode rather than the physical interface configuration modes used for the
          FastEthernet and GigabitEthernet ports.
        </blockquote>
      </td>
      <td class="content code">Switch(config-if)#</td>
    </tr>
    <tr>
      <td class="centered">Config-VLAN</td>
      <td class="content">
        Config-VLAN mode:
        <ul>
          <li>Can perform all VLAN configuration tasks.</li>
          <li>Applies changes immediately.</li>
        </ul>
        <blockquote class="info">
          Do not confuse the Config-VLAN mode with the VLAN interface configuration mode.
        </blockquote>
      </td>
      <td class="content code">Switch(config-vlan)#</td>
    </tr>
    <tr>
      <td class="centered">VLAN Configuration</td>
      <td class="content">
        VLAN configuration mode:
        <ul>
          <li>Allows you to configure a subset of VLAN features.</li>
          <li>Does not apply changes until you save them, either before or while exiting the configuration mode.</li>
          <li>Does not store changes in the regular switch configuration file.</li>
        </ul>
        <blockquote class="info">
          For most modern Cisco switches, it is recommended that you configure VLAN parameters from config-vlan mode, as VLAN
          configuration mode is being deprecated (phased out).
        </blockquote>
      </td/>
      <td class="content code">Switch(vlan)#</td>
    </tr>
    <tr>
      <td class="centered">Line Configuration</td>
      <td class="content"><span class="content">Use Line Configuration mode to configure parameters for the terminal line, such as
      the console, Telnet, and SSH lines.</span></td>
      <td class="content code">Switch(config-line)#</td>
    </tr>
  </tbody></table>
</div>

## Switch Configuration Commands List

<div id="TextViewer-root" class="TextViewer-root">
  <p>The following table lists common switch configuration commands:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="contentheader">Command</td>
        <td class="contentheader">Action</td>
      </tr>
      <tr>
        <td class="content code">switch(config)#interface FastEthernet 0/14<br>
        <br>
        switch(config)#interface GigabitEthernet 0/1</td>
        <td class="content">Moves to interface configuration mode.</td>
      </tr>
      <tr>
        <td class="content code">switch(config)#interface range fastethernet 
		0/14 - 24<br>
        <br>
        switch(config)#interface range gigabitethernet 0/1 - 4<br>
        <br>
        switch(config)#interface range fa 0/1 - 4 , 7 - 10<br>
        <br>
        switch(config)#interface range fa 0/8 - 9 , gi 0/1 - 2</td>
        <td class="content">Moves to configuration mode for a range of 
		interfaces.</td>
      </tr>
      <tr>
        <td class="content code">switch(config-if)#speed 10<br>
        <br>
        switch(config-if)#speed 100<br>
        <br>
        switch(config-if)#speed 1000<br>
        <br>
        switch(config-if)#speed auto</td>
        <td class="content">Sets the port speed on the interface.</td>
      </tr>
      <tr>
        <td class="content code">switch(config-if)#duplex half<br>
        <br>
        switch(config-if)#duplex full<br>
        <br>
        switch(config-if)#duplex auto</td>
        <td class="content">Sets the duplex mode on the interface.</td>
      </tr>
      <tr>
        <td class="content code">switch(config-if)#no shutdown<br>
        <br>
        switch(config-if)#shutdown</td>
        <td class="content">Enables or disables the interface.</td>
      </tr>
      <tr>
        <td class="content code">switch#show interface status</td>
        <td class="content">Shows the interface status of all ports.</td>
      </tr>
      <tr>
        <td class="content code">switch#show ip interface brief</td>
        <td class="content">Shows the line and protocol status of all ports.</td>
      </tr>
    </tbody>
  </table>

  <h3 style="color:#F96302">Switch Configuration Facts</h3>
<p>Important facts about switch configuration include the following:</p>

  <ul>
    <li>All switch ports are enabled (no shutdown) by default.</li>
    <li>Port numbering on some switches begins at 1, not 0. For example, <b>
	FastEthernet 0/1</b> is the first FastEthernet port on a switch.</li>
    <li>Through auto-negotiation, the 10/100/1000 ports configure themselves to 
	operate at the speed of attached devices. If the attached ports do not 
	support auto-negotiation, you can explicitly set the speed and duplex 
	parameters.</li>
    <li>Some switches always use the <i>store-and-forward</i> switching method. 
	On other models, you may be able to configure the switching method.</li>
    <li>If the speed and duplex settings are set to <b>auto</b>, the switch&nbsp; 
	uses auto-MDIX to sense the cable type (crossover or straight-through) 
	connected to the port and automatically adapts itself to the cable type 
	used. When you manually configure the speed or duplex setting, it disables 
	auto-MDIX, so you need to be sure you use the correct cable.</li>
    <li>By default, the link speed and duplex configurations for Ethernet 
	interfaces in Cisco devices are set using IEEE 802.3u auto-negotiation. The 
	interface negotiates with remote devices to determine the correct settings. 
	However, you can disable auto-negotiation con the Cisco device and other 
	Ethernet network hosts and manually assign static values. Devices with 
	auto-negotiation enabled try to negotiate link speed and duplexing, but get 
	no response. When auto-negotiation fails, Cisco devices that have 
	auto-negotiation enabled default to the following:
      <ul>
        <li>The interface attempts to sense the link speed. If it cannot, it 
		uses the slowest link speed supported on the interface (usually 10 
		Mbps).</li>
        <li>If the link speed selected is 10 Mbps or 100 Mbps, half-duplex is 
		used. If it is 1000 Mbps, full-duplex is used.</li>
      </ul>
    </li>
  </ul>
</div>

## Virtual LANs

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>What are two advantages of creating VLANs on your network?</li>
      <li>You have two VLANs configured on a single switch. How many broadcast domains are there? How many collision domains are
      there?</li>
      <li>What happens if two devices on the same switch are assigned to different VLANs?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Create VLANs.</li>
      <li>Explore VLANs.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">VLAN</td>
      <td class="content">A VLAN (Virtual Local Network) is a group of devices on one or more local area networks (LAN) that are
      configured to communicate as if they were attached to the same wire when, in fact, they could be located on a number of
      different LAN segments.</td>
    </tr>
    <tr>
      <td class="centered">VLAN ID</td>
      <td class="content">Switches use VLAN identifications (IDs) to route VLAN traffic. VLAN IDs are appended to the header of
      each frame.<br>
      In addition, VLAN IDs allow switches to identify which VLAN the frame belongs to and are used for inter-switch traffic.<br>
      &nbsp;</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>A virtual LAN (VLAN) uses switch ports to define a broadcast domain. When 
	you define a VLAN, you assign devices on different switch ports to a 
	separate logical (or virtual) LAN. Although a switch can support multiple 
	VLANs, each switch port can only be assigned to one VLAN at a time. The 
	following graphic shows a single-switch VLAN configuration:</p>

  <p><img src="https://cdn.testout.com/_version_5012/netpro2018v5-en-us/en-us/resources/text/swi_vfct/swi_vfct.jpg" border="0"></p>

  <p>In the single-switch VLAN configuration above, the following is true:</p>

  <ul>
    <li>FastEthernet ports 0/1 and 0/2 are members of VLAN 1.</li>
    <li>FastEthernet ports 0/3 and 0/4 are members of VLAN 2.</li>
    <li>Workstations in VLAN 1 cannot communicate with workstations in VLAN 2 
	even though they are connected to the same physical switch. Communications 
	between VLANs requires a router, just as with physical LANs.</li>
    <li>Two broadcast domains are defined, each of which corresponds to one of 
	the VLANs.</li>
    <li>On Cisco switches, all ports are members of VLAN 1 by default.</li>
  </ul>

  <h3 style="color:#F96302">VLAN IDs</h3>

  <p>Switches use VLAN IDs to route VLAN traffic. VLAN IDs:</p>

  <ul>
    <li>Are appended to the header of each frame.</li>
    <li>Allow switches to identify which VLAN the frame belongs to.</li>
    <li>Are used for inter-switch traffic.</li>
  </ul>

  <blockquote class="info">
    VLAN IDs are only understood by switches. VLAN IDs are added and removed by 
	switches, not the clients.
  </blockquote>

  <h3 style="color:#F96302">VLAN Switch Benefits</h3>

  <p>VLANs with switches offer many administrative benefits. You can:</p>

  <ul>
    <li>Create virtual LANs based on criteria other than physical location (such 
	as workgroup, protocol, or service).</li>
    <li>Simplify device moves (devices are moved to new VLANs by modifying the 
	port assignment).</li>
    <li>Control broadcast traffic and create collision domains based on logical 
	criteria.</li>
    <li>Control security (isolate traffic within a VLAN).</li>
    <li>Load-balance network traffic (divide traffic logically rather than 
	physically).</li>
  </ul>

  <blockquote class="info">
    VLANs are commonly used with Voice over IP (VoIP) to separate voice traffic 
	from data traffic. Traffic on the voice VLAN can be given a higher priority 
	to ensure timely delivery.
  </blockquote>
</div>

## VLAN Commands List

<div id="TextViewer-root" class="TextViewer-root">
  <p>To configure a simple VLAN, first create the VLAN, then assign ports to 
	that VLAN. The following table shows common VLAN configuration commands:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="contentheader">Command</td>
        <td class="contentheader">Action</td>
      </tr>
      <tr>
        <td class="Content code">switch(config)#vlan <i>[1-4094]</i><br>
        <br>
        switch(config-vlan)#name <i>[unique_name]</i></td>
        <td class="content">
          Defines a VLAN.<br>
          Gives the VLAN a name.
          <blockquote class="info">
            Naming the VLAN is optional. VLAN names must be unique.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="Content code">switch(config)#no vlan <i>[1-4094]</i></td>
        <td class="content">
          Deletes a VLAN.
          <blockquote class="info">
            When you delete a VLAN, all ports assigned to the deleted VLAN 
			remain associated with it and are, therefore, inactive. After a VLAN 
			is deleted, you must reassign its ports to an appropriate VLAN.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="Content code">switch(config-if)#switchport access vlan <i>
		[1-4094]</i></td>
        <td class="content">
          Assigns ports to the VLAN.<br>
          <blockquote class="info">
            If you assign a port to a VLAN that does not exist, the VLAN is 
			created automatically.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="Content code">switch#show vlan<br>
        <br>
        switch#show vlan brief</td>
        <td class="content">Shows a list of VLANs on the system.</td>
      </tr>
      <tr>
        <td class="Content code">switch#show vlan id <i>[1-4064]</i></td>
        <td class="content">Shows information for a specific VLAN.</td>
      </tr>
    </tbody>
  </table>

  <h4 class="subtitle">Example</h4>

  <p>The following commands create VLAN 12, name it IS_VLAN, identify port 0/12 
	as having only workstations attached to it, and assign the port to VLAN 12.</p>

  <blockquote class="code">
    switch#config t<br>
    switch(config)#vlan 12<br>
    switch(config-vlan)#name IS_VLAN<br>
    switch(config-vlan)#interface fast 0/12<br>
    switch(config-if)#switchport access vlan 12
  </blockquote>
</div>

## Trunking

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>What is trunking?</li>
      <li>Why is trunking important to VLAN configuration?</li>
      <li>What protocol does a Cisco switch use to automatically detect trunk ports?</li>
      <li>By default, traffic from which VLANs are allowed on trunk ports?</li>
      <li>What is the default configuration of most Cisco switches?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure trunking</li>
      <li>Configure the native VLAN</li>
      <li>Configure allowed VLANs</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">VTP</td>
      <td class="content">VLAN Trunking Protocol (VTP) is a Cisco proprietary protocol that propagates the definition of Virtual
      Local Area Networks (VLAN) on the whole local area network. Trunking occurs when you configure VLANs that span multiple
      switches.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>Trunking occurs when you configure VLANs that span multiple switches, as 
	shown in the following diagram:</p>

  <p><img src="https://cdn.testout.com/_version_5012/netpro2018v5-en-us/en-us/resources/text/swi_tfct/swi_tfct.jpg" border="0"></p>

  <p>In this example, each switch has two VLANs configured with one port on each 
	VLAN. Workstations in VLAN 1 can only communicate with other workstations in 
	VLAN 1. This means that workstations connected to the same switch in this 
	example cannot communicate directly with each other. Communications between 
	workstations within each VLAN must pass through the trunk link to the other 
	switch.</p>
<h3 style="color:#F96302">Trunking Facts</h3>
  <p>Important facts regarding trunking and VLANs include the following:</p>

  <ul>
    <li>Access ports are connected to endpoint devices (such as workstations), 
	while trunk ports are connected to other switches.</li>
    <li>An access port can be a member of only a single VLAN.</li>
    <li>Trunk ports are members of all VLANs on the switch by default.</li>
    <li>Any port on a switch can be configured as a trunk port.</li>
    <li>By default, trunk ports carry traffic for all VLANs between switches. 
	However, you can reconfigure a trunk port so that it carries only specific 
	VLANs on the trunk link.</li>
  </ul>

  <p>When trunking is used, frames that are sent over a trunk port are tagged 
	with the VLAN ID number so the receiving switch knows which VLAN the frame 
	belongs to. In VLAN tagging:</p>

  <ul>
    <li>Tags are appended by the first switch in the path and removed by the 
	last.</li>
    <li>Only VLAN-capable devices understand the frame tag.</li>
    <li>Tags must be removed before a frame is forwarded to a non-VLAN capable 
	device.</li>
  </ul>

  <p>A trunking protocol defines the process that switches use to tag frames 
	with a VLAN ID. One widely implemented trunking protocol is the IEEE 802.1Q 
	standard, which supports a wide range of switches from many device 
	manufacturers. 802.1Q supports VLAN numbers 1 through 4094.</p>

  <p>802.1Q trunking does not tag frames from the default VLAN, but does tag 
	frames from all other VLANs. For example, suppose VLAN 1 is the default VLAN 
	on a switch (the default setting on most Cisco switches). In this 
	configuration, any frame on VLAN 1 that is placed on a trunk link is not 
	assigned a VLAN tag. If a switch receives a frame on a trunk port that 
	doesn't have a VLAN tag, the frame is automatically put on VLAN 1.</p>

  <blockquote class="info">
    When using switches from multiple vendors in the same network, be sure that 
	each device supports the 802.1Q standard.
  </blockquote>

  <p>The VLAN Trunking Protocol (VTP) simplifies VLAN configuration on a 
	multi-switch network by propagating configuration changes between switches. 
	For VTP to work, the switches must be connected by trunk links. With VTP, 
	switches are configured in one of the following configuration modes:</p>

  <ul>
    <li>A switch in <i>server mode</i> is used to modify the VLAN configuration. 
	The switch then advertises VTP information to other switches in the network.</li>
    <li>A switch in <i>client mode</i> receives changes from a VTP server switch 
	and passes that information on to other switches. Changes cannot be made to 
	the local VLAN configuration on a client switch.</li>
    <li>A switch in <i>transparent mode</i> allows local configuration of VLAN 
	information, but it does not update its configuration with information from 
	other switches. Likewise, local VLAN information is not advertised to other 
	switches. However, VTP information received on the network is passed on to 
	other switches.</li>
  </ul>

  <p>By default, most managed switches are preconfigured to operate in server 
	mode. If you do not intend to use VTP, configure your switches to use 
	transparent mode.</p>
</div>

## Trunking Commands List

<div id="TextViewer-root" class="TextViewer-root">
  <p>The following table lists important commands for configuring and monitoring 
	trunking on a Cisco switch:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="contentheader">Command</td>
        <td class="contentheader">Action</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#switchport mode trunk</td>
        <td class="content">Enables trunking on the interface.</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#switchport mode access</td>
        <td class="content">Configures an interface as an access port, which 
		disables trunking on the interface (if it was previously configured).</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#switchport trunk 
		encapsulation dot1q<br>
        <br>
        Switch(config-if)#switchport trunk encapsulation negotiate</td>
        <td class="content">
          <p>Sets the trunking protocol to 802.1Q.</p>
          <p>Allows the trunking protocol to be negotiated between switches.</p>
        </td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#switchport trunk native vlan <i>
		[vlan_id]</i></td>
        <td class="content">Configures the VLAN that sends and receives untagged 
		traffic on the trunk port when the interface is in 802.1Q trunking mode.</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#switchport trunk allowed vlan 
		all<br>
        <br>
        Switch(config-if)#switchport trunk allowed vlan add <i>[vlan_id]</i></td>
        <td class="content">Defines which VLANs are allowed to communicate over 
		the trunk.</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#switchport trunk allowed vlan 
		remove <i>[vlan_id]</i></td>
        <td class="content">Removes a VLAN from a trunk link.</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#switchport access vlan <i>
		[number]</i></td>
        <td class="content">Assigns an interface to a VLAN.</td>
      </tr>
      <tr>
        <td class="content code">Switch#show interface trunk<br>
        <br>
        Switch#show interface fa0/1 trunk</td>
        <td class="content">
          Shows interface trunking information with the following:
          <ul>
            <li>Mode</li>
            <li>Encapsulation</li>
            <li>Trunking status</li>
            <li>VLAN assignments</li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>

  <h4 class="subtitle">Example</h4>

  <p>Two distribution layer switches, SW1 and SW2, are connected through their 
	respective Gi0/1 interfaces. The following commands configure a trunk link 
	between the switches:</p>

  <blockquote class="code">
    SW1&gt;ena<br>
    SW1#conf t<br>
    SW1(config)#int gi 0/1<br>
    SW1(config-if)#switchport mode trunk
  </blockquote>

  <blockquote class="code">
    SW2&gt;ena<br>
    SW2#conf t<br>
    SW2(config)#int gi 0/1<br>
    SW2(config-if)#switchport mode trunk
  </blockquote>
</div>

## Spanning Tree Protocol 

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>Why does root switch selection never require a tie breaker?</li>
      <li>When would you modify an STP mode?</li>
      <li>How does PVST+ differ from Rapid PVST+?</li>
      <li>How do ports work in a multiple VLAN environment?</li>
      <li>How are root bridges designated in a multiple VLAN environment?</li>
      <li>What happens during STP convergence?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure STP</li>
      <li>Select a root bridge</li>
      <li>Configure Rapid PVST+</li>
      <li>Find STP Info</li>
      <li>Configure EtherChannels</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Switching Loop</td>
      <td class="content">Many networks implement redundant paths between multiple switches to create fault tolerance. However,
      providing redundant paths between segments could cause frames to pass between the redundant paths endlessly. This condition
      is known as a switching loop.</td>
    </tr>
    <tr>
      <td class="centered">Spanning Tree Protocol<br>
      (STP)</td>
      <td class="content">
        <p>The Spanning Tree Protocol (STP) is a network protocol that builds a 
		loop-free logical topology for Ethernet networks. </p>
      </td>
    </tr>
    <tr>
      <td class="centered">Root Bridge</td>
      <td class="content">The root bridge is the master bridge, or controlling bridge.</td>
    </tr>
    <tr>
      <td class="centered">Designated Bridge</td>
      <td class="content">A designated bridge is any other device that participates in forwarding packets through the network.</td>
    </tr>
    <tr>
      <td class="centered">Backup Bridge</td>
      <td class="content">All redundant devices are classified as backup 
		bridges. They listen to network traffic and build the bridge database. 
		However, they do not forward packets. They can take over if the root bridge 
		or a designated bridge
      fails.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>Many networks implement redundant paths between multiple switches to create 
	fault tolerance. However, providing redundant paths between segments could 
	cause frames to pass between the redundant paths endlessly. This condition 
	is known as a <i>switching loop</i>.</p>

  <p>To prevent switching loops, the IEEE 802.1d committee defined the Spanning 
	Tree Protocol (STP). With STP, one switch for each route is assigned as the 
	designated bridge. Only the designated bridge can forward packets. Redundant 
	switches are assigned as backups.</p>

  <p>The spanning tree protocol:</p>

  <ul>
    <li>Eliminates loops.</li>
    <li>Provides redundant paths between devices.</li>
    <li>Enables dynamic role configuration.</li>
    <li>Recovers automatically from a topology change or device failure.</li>
    <li>Identifies the optimal path between any two network devices.</li>
  </ul>

  <p>The spanning tree protocol uses a spanning tree algorithm (STA) to 
	calculate the best loop-free path through a network by assigning a role to 
	each bridge or switch. The bridge role determines how the device functions 
	in relation to other devices and whether the device forwards traffic to 
	other segments. </p>

<h3 style="color:#F96302">Bridge Role Types</h3>
<p>The following table describes the three types of bridge roles:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Role</td>
        <td class="contentheader">Characteristics</td>
      </tr>
      <tr>
        <td class="centered">Root bridge</td>
        <td class="content">
          The <i>root bridge</i> is the master bridge, or controlling bridge.
          <ul>
            <li>There is only one root bridge in the network. <span class="content">
			The root bridge is the logical center of the spanning tree topology 
			in a switched network.</span></li>
            <li>The root bridge is determined by the switch with the lowest 
			bridge ID (BID):
              <ul>
                <li>The bridge ID is composed of two parts—a bridge priority 
				number and the MAC address assigned to the switch.</li>
                <li>The default priority number for all switches is 32,768. This 
				means the switch with the lowest MAC address becomes the root 
				bridge unless you customize the priority values.</li>
                <li>You can manually configure the priority number to force a 
				specific switch to become the root switch.</li>
              </ul>
            </li>
            <li>The root bridge periodically broadcasts configuration messages. 
			These messages are used to select routes and reconfigure the roles 
			of other bridges if necessary.</li>
            <li>All ports on a root bridge forward messages to the network.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Designated bridge</td>
        <td class="content">
          A <i>designated bridge</i> is any other device that participates in 
			forwarding packets through the network.
          <ul>
            <li>Designated bridges are selected automatically by exchanging 
			bridge configuration packets.</li>
            <li>To prevent bridge loops, there is only one designated bridge per 
			segment.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Backup bridge</td>
        <td class="content">
          All redundant devices are classified as <i>backup bridges</i>.
          <ul>
            <li>They listen to network traffic and build the bridge database. 
			However, they will not forward packets.</li>
            <li>They can take over if the root bridge or a designated bridge 
			fails.</li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>


<h3 style="color:#F96302">Port States</h3>
<p>Devices send special packets called Bridge Protocol Data Units (BPDUs) out 
each port. BPDUs sent to and received from other bridges are used to determine 
bridge roles and port states, verify that neighbor devices are still 
functioning, and recover from network topology changes. During the negotiation 
process and normal operations, each switch port is in one of the following 
states:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Port State</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Disabled</td>
        <td class="content">A port in the disabled state is powered on but does 
		not participate in forwarding or listening to network messages. A bridge 
		must be manually placed in the disabled state.</td>
      </tr>
      <tr>
        <td class="centered">Blocking</td>
        <td class="content">When a device is first powered on, its ports are in 
		the blocking state. Backup bridge ports are always in the blocking 
		state. Ports in a blocking state receive packets and BPDUs sent to all 
		bridges, but they will not process any other packets.</td>
      </tr>
      <tr>
        <td class="centered">Listening</td>
        <td class="content">The listening state is a transitory state between 
		blocking and learning. The port remains in the listening state for a 
		specific period of time. This time period allows network traffic to 
		settle down after a change has occurred. For example, if a bridge goes 
		down, all other bridges go into the listening state for a period of 
		time. During this time, the bridges redefine their roles.</td>
      </tr>
      <tr>
        <td class="centered">Learning</td>
        <td class="content">A port in the learning state receives packets and 
		builds the bridge database (associating MAC addresses with ports). A 
		timer is also associated with this state. The port goes to the 
		forwarding state after the timer expires.</td>
      </tr>
      <tr>
        <td class="centered">Forwarding</td>
        <td class="content">The root bridge and designated bridges are in the 
		forwarding state when they can receive and forward packets. A port in 
		the forwarding state can learn and forward. All ports of the root switch 
		are in the forwarding state.</td>
      </tr>
    </tbody>
  </table>

 
<h3 style="color:#F96302">Port Types</h3>
<p>During the configuration process, ports on each switch are configured as one 
of the following types:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Port Type</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Root Port</td>
        <td class="content">
          The port on a designated switch with the lowest port cost back to the 
			root bridge is identified as the <i>root port</i>.
          <ul>
            <li>Each designated switch has a single root port (a single path 
			back to the route bridge).</li>
            <li>Root ports are in the forwarding state.</li>
            <li>The root bridge does not have a root port.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Designated Port</td>
        <td class="content">
          One port on each segment is identified as the <i>designated port</i>. 
			The designated port identifies which port on the segment is allowed 
			to send and receive frames.
          <ul>
            <li>All ports on the root bridge are designated ports (unless the 
			switch port loops back to a port on the same switch).</li>
            <li>Designated ports are selected based on the lowest path cost to 
			get back to the root switch. Default IEEE port costs include the 
			following:
              <ul>
                <li>10 Mbps = 1000</li>
                <li>100 Mbps = 19</li>
                <li>1 Gbps = 4</li>
                <li>10 Gbps = 2</li>
              </ul>
            </li>
            <li>If two switches have the same cost, the switch with the lowest 
			priority becomes the designated switch, and its port becomes the 
			designated port.</li>
            <li>If two ports have the same cost, the port on the switch with the 
			lowest port ID becomes the designated port.
              <ul>
                <li>The port ID is derived from two numbers, the port priority 
				and the port number.</li>
                <li>The port priority ranges from 0–255, and its default setting 
				is 128.</li>
                <li>The port number is the number of the switch's port. For 
				example, the port number for Fa0/3 is 3.</li>
                <li>With the default port priority setting, the lowest port 
				number becomes the designated port.</li>
              </ul>
            </li>
            <li>Designated ports are used to send frames back to the root 
			bridge.</li>
            <li>Designated ports are in the forwarding state.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Blocking Port</td>
        <td class="content">A blocking port is any port that is not a root or a 
		designated port. A blocking port is in blocking state.</td>
      </tr>
    </tbody>
  </table>

<h3 style="color:#F96302">Spanning Tree Configuration</h3>
<p>Devices participating in the spanning tree protocol use the following process 
to configure themselves:</p>

  <ol>
    <li>At startup, switches send BPDUs out each port.</li>
    <li>Switches read the bridge ID contained in the BPDUs to elect (identify) a 
	single root bridge (the device with the lowest bridge ID). All of the ports 
	on the root bridge become designated ports.</li>
    <li>Each switch identifies its root port (the port with the lowest cost back 
	to the root bridge).</li>
    <li>Switches on redundant paths identify a designated switch for each 
	segment. A designated port is also identified on each designated switch.</li>
    <li>Remaining switch ports that are not root or designated ports are put in 
	the blocking state to eliminate loops.</li>
    <li>After configuration, switches periodically send BPDUs to ensure 
	connectivity and discover topology changes.</li>
  </ol>

  <p>The following table lists commands used to configure spanning tree:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="contentheader">Command</td>
        <td class="contentheader c1">Function</td>
      </tr>
      <tr>
        <td class="content code">Switch(config)#spanning-tree mode {pvst | 
		rapid-pvst}</td>
        <td class="content">
          Sets the spanning tree mode.
          <ul>
            <li>PVST+ (Per VLAN Spanning Tree Protocol), also known as PVSTP, is 
			a Cisco proprietary protocol used on Cisco switches.</li>
            <li>Rapid PVST+ is Cisco's proprietary version of Rapid STP, which 
			is based on the 802.1w standard.</li>
          </ul>
          <blockquote class="info">
            PVST+ and Rapid PVST+ are the same except that Rapid PVST+ uses a 
			rapid convergence based on the 802.1w standard. To provide rapid 
			convergence, Rapid PVST+ deletes learned MAC address entries on a 
			per-port basis after receiving a topology change.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="content code">Switch(config)#spanning-tree vlan <i>[1-4094]</i> 
		root primary</td>
        <td class="content">Forces the switch to be the root of the spanning 
		tree.</td>
      </tr>
      <tr>
        <td class="content code">Switch(config)#spanning-tree vlan <i>[1-4094]</i> 
		cost <i>[1 - 200000000]</i></td>
        <td class="content">
          Manually sets the cost. The cost range value depends on the path-cost 
			calculation method:
          <ul>
            <li>Short method range: 1 - 65536.</li>
            <li>Long method range: 1 - 200000000.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="content code">Switch(config)#spanning-tree vlan <i>[1-4094]</i> 
		priority <i>[0-61440]</i></td>
        <td class="content">
          Manually sets the bridge priority number as follows:
          <ul>
            <li>The priority value ranges between 0 and 61440.</li>
            <li>Each switch has the default priority of 32768.</li>
            <li>Priority values are set in increments of 4096. If you enter 
			another number, your value is rounded to the closest increment of 
			4096 or you are prompted to enter a valid value.</li>
            <li>The switch with the lowest priority number becomes the root 
			bridge.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="content code">Switch(config)#no spanning-tree vlan <i>
		[1-4094]</i></td>
        <td class="content">Disables spanning tree on the selected VLAN.</td>
      </tr>
      <tr>
        <td class="content code">Switch#show spanning-tree</td>
        <td class="content">
          Shows spanning tree configuration information, including the 
			following:
          <ul>
            <li>Root bridge priority and MAC address</li>
            <li>The cost to the root bridge</li>
            <li>Local switch bridge ID and MAC address</li>
            <li>The role and status of all local interfaces</li>
            <li>The priority and number for each interface</li>
          </ul>To verify that spanning tree is working, look for an entry 
			similar to the following for each VLAN:
          <blockquote class="code">
            Spanning tree enabled protocol ieee
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="content code">Switch#show spanning-tree vlan <i>[1-4094]</i> 
		root</td>
        <td class="content">
          Shows information about the root bridge for a specific VLAN. 
			Information shown includes:
          <ul>
            <li>The root bridge ID, including the priority number and the MAC 
			address</li>
            <li>The cost to the root bridge from the local switch</li>
            <li>The local port that is the root port</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="content code">Switch#show spanning-tree vlan <i>[1-4094]</i> 
		bridge</td>
        <td class="content">Shows spanning tree configuration information about 
		the local switch for the specified VLAN. Information includes the local 
		bridge ID, including the priority and MAC address.</td>
      </tr>
    </tbody>
  </table>

 	<h3 style="color:#F96302">Shortest Path Bridging Protocol</h3>
<p>Even though STP is great at eliminating switching loops, it has a key 
weakness: it allows only a single active path between two switches at any given 
time. If that active link goes down, it can sometimes take 30 seconds or more 
for STP to detect that the link has gone down before it activates a redundant 
link. To address this weakness, a new protocol, <i>Shortest Path Bridging</i> 
(SPB), has been developed to eventually replace STP. SPB is a routing protocol 
defined in the IEEE 802.1aq standard that adds routing functions to Layer 2 
switching. SPB uses a link-state routing protocol to allow switches to learn the 
shortest paths through a switched Ethernet network and dynamically adjust those 
paths as the topology changes, just like a Layer 3 router does.</p>

  <p>SPB addresses this issue by applying Layer 3 routing protocols to Layer 2 
	switches. This allows those switches to actually route Ethernet frames 
	between switches, just as Layer 3 protocols route packets between routers. 
	By doing this, SPB allows multiple links between switches to be active at 
	the same time without creating a switching loop. This functionality is 
	designed to eliminate the time lag associated with failed links managed by 
	STP. If a link between switches goes down on a network that uses SPB, the 
	frames can be immediately re-routed to the destination segment by using 
	redundant links between switches that are already active and able to forward 
	frames.</p>
</div>

## EtherChannel

<div id="TextViewer-root" class="TextViewer-root">
  <p>EtherChannel combines multiple ports on a Cisco switch into a single 
	logical link between two switches. With EtherChannel:</p>
  <ul>
    <li>You can combine 2–8 ports into a single link.</li>
    <li>All links in the channel group are used for communication between the 
	switches.</li>
    <li>Bandwidth between switches is increased.</li>
    <li>Automatic redundant paths between switches are established. If one link 
	fails, communication will still occur over the other links in the group.</li>
    <li>Spanning tree convergence times are reduced.</li>
  </ul>

  <p><img src="https://cdn.testout.com/_version_5012/netpro2018v5-en-us/en-us/resources/text/trbetherchannel/trbetherchannel_01.png"><img src="https://cdn.testout.com/_version_5012/netpro2018v5-en-us/en-us/resources/text/trbetherchannel/trbetherchannel_02.png"></p>

<h3 style="color:#F96302">&nbsp;</h3>
<h3 style="color:#F96302">EtherChannel Configuration Protocols</h3>
<p>Cisco switches can use the following protocols for EtherChannel 
configuration:</p>

  <table border="1">
    <tbody><tr class="header">
      <td class="centered">Protocol</td>
      <td class="contentheader">Description</td>
    </tr>
    <tr>
      <td class="centered">Port Aggregation Protocol (PAgP)</td>
      <td class="content">
        Port Aggregation Protocol prevents loops, limits packet loss due to 
		misconfigured channels, and aids in network reliability. PAgP operates 
		in the following modes:
        <ul>
          <li>Auto mode places the port into a passive negotiating state and 
			forms an EtherChannel if the port receives PAgP packets. While in 
			this mode, the port does not initiate the negotiation.</li>
          <li>Desirable mode places the port in a negotiating state to form an 
			EtherChannel by sending PAgP packets. A channel is formed with 
			another port group in either the auto or desirable mode.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td class="centered">Link Aggregation Control Protocol (LACP)</td>
      <td class="content">
        Link Aggregation Control Protocol is based on the 802.3ad standard and 
		has similar functions to PAgP. LACP is used when configuring 
		EtherChannel between Cisco switches and non-Cisco switches that support 
		802.3ad. LACP operates in the following modes:
        <ul>
          <li>Passive mode places the port into a passive negotiating state and 
			forms an EtherChannel if the port receives LACP packets. While in 
			this mode, the port does not initiate the negotiation.<br></li>
          <li>Active mode places the port in a negotiating state to form an 
			EtherChannel by sending LACP packets. A channel is formed with 
			another port group in either the active or passive mode.</li>
        </ul>
      </td>
    </tr>
  </tbody></table>

<h3 style="color:#F96302">&nbsp;</h3>
<h3 style="color:#F96302">EtherChannel Configuration Commands</h3>
<p>The following table shows common commands that configure EtherChannel:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="contentheader">Command</td>
        <td class="contentheader">Action</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#channel-protocol lacp<br>
        <br>
        Switch(config-if)#channel-protocol pagp</td>
        <td class="content">Selects the EtherChannel protocol on the interface.</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#channel-group <i>[1-8]</i> 
		mode auto<br>
        <br>
        Switch(config-if)#channel-group <i>[1-8]</i> mode desirable</td>
        <td class="content">Selects the PAgP mode on the interface.</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#channel-group <i>[1-8]</i> 
		mode active<br>
        <br>
        Switch(config-if)#channel-group <i>[1-8]</i> mode passive</td>
        <td class="content">Selects the LACP mode on the interface.</td>
      </tr>
      <tr>
        <td class="content code">Switch(config-if)#no channel-group <i>[1-8]</i></td>
        <td class="content">Disables EtherChannel on the interface.</td>
      </tr>
      <tr>
        <td class="content code">Switch#show etherchannel</td>
        <td class="content">Displays EtherChannel details on the switch.</td>
      </tr>
      <tr>
        <td class="content code">Switch#show etherchannel summary</td>
        <td class="content">Displays EtherChannel information for a channel with 
		a one-line summary per channel group.</td>
      </tr>
    </tbody>
  </table>

  <blockquote class="info">
    Each channel group has its own number. All ports assigned to the same 
	channel group are viewed as a single logical link.
  </blockquote>

  <h4 class="subtitle">Examples</h4>

  <p>The following commands configure GigabitEthernet 0/1 and 0/2 interfaces to 
	actively initiate the negotiation of an EtherChannel with the PAgP protocol 
	and a channel group of 5:</p>

  <blockquote class="code">
    Switch&gt;ena<br>
    Switch#conf t<br>
    Switch(config)#int range gi 0/1 - 2<br>
    Switch(config-if-range)#channel-protocol pagp<br>
    Switch(config-if-range)#channel-group 5 mode desirable
  </blockquote>

  <p>The following commands configure FastEthernet 0/1 through 0/4 interfaces to 
	form an EtherChannel with the LACP protocol if the other device actively 
	initiates the EtherChannel connection:</p>

  <blockquote class="code">
    Switch&gt;ena<br>
    Switch#conf t<br>
    Switch(config)#int range ga 0/1 - 4<br>
    Switch(config-if-range)#channel-protocol lacp<br>
    Switch(config-if-range)#channel-group 3 mode passive<br>
    Switch(config-if-range)#duplex full
  </blockquote>

  <h3 style="color:#F96302">&nbsp;</h3>
	<h3 style="color:#F96302">Troubleshoot EtherChannel Configuration</h3>
<p>Use the following guidelines to troubleshoot an EtherChannel configuration:</p>

  <ul>
    <li>Make sure that all ports in an EtherChannel use the same protocol (PAgP 
	or LACP):
      <ul>
        <li>If the <b>channel-group</b> command is used with the <b>desirable</b> 
		option on one switch (PAgP), the other switch must use either <b>
		desirable</b> or <b>auto</b>.</li>
        <li>If the <b>channel-group</b> command is used with the <b>active</b> 
		option (LACP), the other switch must use either
        <b>active</b> or <b>passive</b>.</li>
      </ul>
    </li>
    <li>Verify that all ports in the EtherChannel have the same speed and duplex 
	mode. LACP requires that the ports operate only in full-duplex mode.</li>
    <li>Check the channel group number. A port cannot belong to more than one 
	channel group at the same time.</li>
    <li>Verify that all ports in the EtherChannel have the same access VLAN 
	configuration or are VLAN trunks with the same allowable VLAN list and the 
	same native VLAN.</li>
    <li>Check the spanning tree configuration. If you do not configure 
	EtherChannel, the spanning tree algorithm identifies each link as a 
	redundant path to the other bridge and puts one of the ports in a blocking 
	state.</li>
    <li>Check the port type and number. You can configure an LACP EtherChannel 
	with up to 16 Ethernet ports of the same type. Up to eight ports can be 
	active, and up to eight ports can be in standby mode.</li>
    <li>Be sure to enable all ports in an EtherChannel. A port in an 
	EtherChannel that is disabled using the <b>shutdown</b>
    interface configuration command is treated as a link failure, and its 
	traffic is transferred to one of the remaining ports in the EtherChannel.</li>
  </ul>

  <blockquote class="info">
    Do not configure more than six EtherChannels on one switch.
  </blockquote>
</div>

## Switch Troubleshooting

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>You have a network connected by switches with a single device connected to each switch port. Why would you be surprised
      to see collisions on this network?</li>
      <li>What is a duplex mismatch?</li>
      <li>What conditions lead to a broadcast storm?</li>
      <li>How can you prevent switching loops from forming?</li>
      <li>You moved a device from one switch port to another, and now it cannot communicate with any other device on the network.
      The switch link lights are lit. What switch configuration should you check?</li>
      <li>Other than the switch configuration, what should you check if you see excessive frame errors on the switch?</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>
  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Broadcast Storm</td>
      <td class="content">A broadcast storm is excessive broadcast traffic that 
		renders normal network communications impossible. </td>
    </tr>
    <tr>
      <td class="centered">Collisions</td>
      <td class="content">A collision occurs when two devices that share the 
		same media segment transmit at the same time. </td>
    </tr>
    <tr>
      <td class="centered">Duplex Mismatch</td>
      <td class="content">A duplex mismatch occurs when two devices use 
		different duplex settings. For example, when one device tries to 
		transmit using full duplex while the other expects half duplex 
		communications. </td>
    </tr>
    <tr>
      <td class="centered">Frame Errors</td>
      <td class="content">The switch examines incoming frames and only forwards frames that are complete and correctly formed;
      invalid frames are simply dropped. These types of frames are known as frame errors.</td>
    </tr>
  </tbody></table>
</div>

<div id="TextViewer-root" class="TextViewer-root">
  <p>The following table lists several problems you might encounter when 
	managing switches on your network:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Issue</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Bad Port</td>
        <td class="content">A <i>bad port</i> is a faulty or bad interface on a 
		switch. To fix the problem, you need to return the switch back to the 
		supplier and get a replacement. However, if you have plenty of ports on 
		the switch, you can configure the port using '<b>description ** Bad 
		Port **</b>', and then insert a RJ45 single connector into the bad port 
		to occupy the port.</td>
      </tr>
      <tr>
        <td class="centered">Broadcast Storm</td>
        <td class="content">
          A <i>broadcast storm</i> is excessive broadcast traffic that renders 
			normal network communications impossible. The following can cause 
			broadcast storms:
          <ul>
            <li>Switching loops that cause broadcast traffic to circulate 
			endlessly between switches</li>
            <li>Denial of Service (DoS) attacks</li>
          </ul>To reduce broadcast storms, complete the following:
          <ul>
            <li>Run STP to prevent switching loops.</li>
            <li>Implement switches with built-in broadcast storm detection, 
			which limits the bandwidth that broadcast traffic can use.</li>
            <li>Use VLANs to create separate broadcast domains on switches.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Collisions</td>
        <td class="content">
          A <i>collision</i> occurs when two devices that share the same media 
			segment transmit at the same time. In a switched network, collisions 
			should only occur on ports that have more than one device attached 
			(such as a hub with workstations connected to it).
          <ul>
            <li>To eliminate collisions, connect only a single device to each 
			switch port. For example, if a hub is connected to a switch port, 
			replace it with another switch.</li>
            <li>If collisions are still detected, troubleshoot cable and NIC 
			issues.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Duplex Mismatch</td>
        <td class="content">
          A <i>duplex mismatch</i> occurs when two devices use different duplex 
			settings. In this case, one device tries to transmit using full 
			duplex, while the other expects half duplex communications. By 
			default, devices are configured to use auto-negotiation to detect 
			the correct duplex setting to use. If a duplex method cannot be 
			agreed upon, devices default to half duplex.
          <p>A duplex mismatch can occur in the following cases:</p>
          <ul>
            <li>Both devices are configured to use different duplex settings.</li>
            <li>Auto-negotiation does not work correctly on one device.</li>
            <li>One device is configured for auto-negotiation, and the other 
			device is manually configured for full duplex.</li>
          </ul>
          <blockquote class="info">
            Symptoms of a duplex mismatch include very slow network 
			communications. Ping tests might appear to complete correctly, but 
			normal communications work well below the expected speeds, even for 
			half duplex communications.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Frame Errors</td>
        <td class="content">
          The switch examines incoming frames and only forwards frames that are 
			complete and correctly formed; invalid frames are simply dropped. 
			Most switches include logging capabilities to track the number of 
			corrupt or malformed frames. The following are common causes of 
			frame errors:
          <ul>
            <li>Frames that are too long are typically caused by a faulty 
			network card that jabbers (constantly sends garbage data).</li>
            <li>Frames that are too short are typically caused by collisions.</li>
            <li>CRC errors indicate that a frame has been corrupted in transit.</li>
            <li>All types of frame errors can be caused by faulty cables or 
			physical layer devices.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Incorrect VLAN Membership</td>
        <td class="content">
          VLANs create logical groupings of computers based on switch port. 
			Because devices on one VLAN cannot communicate directly with devices 
			in other VLANs, incorrectly assigning a port to a VLAN can prevent a 
			device from communicating through the switch.
          <blockquote class="info">
            With VLAN membership, static port assignment is defined by switch 
			port, not by a MAC address. Connecting a device to a different 
			switch port could change the VLAN membership of the device. On the 
			switch, verify that ports are assigned to the correct VLANs and that 
			any unused VLANs are removed from the switch.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Slow Link Speed</td>
        <td class="content">
          Most network components are capable of supporting multiple network 
			specifications. By default, these devices use the maximum speed 
			supported by all devices on the network.
          <p>If the speed of a segment is lower than expected (for example, 10 
			Mbps instead of 100 Mbps, or 100 Mbps instead of 1000 Mbps), 
			complete the following:</p>
          <ul>
            <li>Check individual devices to verify that they all support the 
			higher speed.</li>
            <li>Check individual devices to see if any are manually configured 
			to use the lower speed.</li>
            <li>Use a cable certifier to verify that the cables meet the rated 
			speeds. Bad cables are often the cause of 1000BaseT networks 
			operating at only 100BaseTX speeds.</li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
</div>

<br/>

# Chapter 7 Routing 
###### [Back to top](#Network-Security-and-Data-Communications)

<table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Packet</td>
      <td class="content">A packet is the payload of an OSI Layer 2 frame. A packet has a header and a payload. The header contains
      the source and destination IP addresses. The payload depends on the protocol that formed the packet.</td>
    </tr>
    <tr>
      <td class="centered">Network</td>
      <td class="content">When used in routing, the term network can be defined as a broadcast domain where all the hosts have the
      same network portion in their IP address. Normally, a LAN fits this more precise definition of a network.</td>
    </tr>
    <tr>
      <td class="centered">Routing Table</td>
      <td class="content">
        The routing table is a database of entries containing:<ul>
          <li>The address of a known network.</li>
          <li>The next hop gateway (router).</li>
          <li>The network interface to reach the next hop gateway.</li>
          <li>A metric or cost that indicates the desirability of the route (Tte lower the metric, the more desirable the
          route).</li>
        </ul>
      </td>
    </tr>
	<tr>
      <td class="centered">Next Hop</td>
      <td class="content">An IP address entry in a router's routing table 
		that specifies the next or closest router in its routing path.</td>
    </tr>
    <tr>
      <td class="centered">Default Route</td>
      <td class="content">The default route is an entry of 0.0.0.0 in a routing 
		table. This entry matches every network.</td>
    </tr>
    <tr>
      <td class="centered">Loopback Entry</td>
      <td class="content">Loopback entries contains loopback addresses, which are 
		used for diagnostics and for troubleshooting the TCP/IP stack. </td>
    </tr>
  </tbody></table>

<div class="TextViewer-container"><div id="TextViewer-root" class="TextViewer-root">
  <p>Routing is the process of moving packet from one network to another using routers. In this lesson you will learn about:</p>

  <ul>
    <li>How routing works</li>
    <li>Static and dynamic routing</li>
    <li>Interior and exterior routing</li>
  </ul>

  <h3 style="color:#F96302">How Routing Works</h3>

  <p>A router is a device that sends packets from one network to another.</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Term</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Packet</td>
        <td class="content">
          A <i>packet</i> is the payload of an OSI layer 2 frame. A packet has a header and a payload.
          <ul>
            <li>The header contains source and destination IP addresses.</li>
            <li>The payload depends on the protocol that formed the packet.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Network</td>
        <td class="content">When used in routing, the term network can be defined as a broadcast domain where all the hosts have
        the same network portion in their IP address. Normally, a LAN fits this more precise definition of a network.</td>
      </tr>
    </tbody>
  </table>

  <p>To perform routing, a router:</p>

  <ul>
    <li>Receives a frame</li>
    <li>Opens the frame's payload, which is an IP packet</li>
    <li>Reads the packet header to find IP addressing information</li>
    <li>Matches the destination network address with entries in its
        routing table creates a new frame using the packet as a payload</li>
    <li>Transmits the new frame to the next hop gateway.</li>
  </ul>

  <p>The following table describes a few important routing terms:</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Term</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Next Hop</td>
        <td class="content">To forward a packet, a router only needs to know next hop information, not the full path to the
        ultimate destination. The <i>next hop</i> is the gateway (router) that the router will to send the packet to.</td>
      </tr>
      <tr>
        <td class="centered">Routing Table</td>
        <td class="content">
          The <i>routing table</i> is a database of entries, each with:
          <ul>
            <li>The address of a known network</li>
            <li>The next hop gateway (router)</li>
            <li>The network interface to reach the next hop gateway</li>
            <li>A metric or cost that indicates the desirability of the route (The lower the metric, the more desirable the
            route.)</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Default Route</td>
        <td class="content">
          The <i>default route</i> is an entry of 0.0.0.0 in a routing table. This entry matches every network. If no other entry
          in the routing table matches the destination IP address in a packet, the router will send the packet to the gateway found
          in the default route.
          <ul>
            <li>The gateway identified in the default route is known as the default gateway.</li>
            <li>If a default route does not exist, the router will drop any packets that do not match an entry in a routing
            table.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Loopback Entry</td>
        <td class="content">Loopback entries contains loopback addresses which are used for diagnostics and for troubleshooting the
        TCP/IP stack. Loopback interfaces are always available. They will continue to run even if other physical interfaces in the
        router are down.</td>
      </tr>
    </tbody>
  </table>

  <h3 style="color:#F96302">Static and Dynamic Routing</h3>

  <p>Routing can be classified by how entries are added to the routing table. There are three types of routing entries—default,
  static and dynamic. You can use default, static and dynamic routing together.</p>

  <p>Information about other networks can be added to the routing table using one of two methods:</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Method</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Static</td>
        <td class="content">
          Static routing entries are manually added to the routing table.
          <ul>
            <li>A route entry of 0.0.0.0 identifies the default entry or default route which is special form of a static
            entry.</li>
            <li>Static entries remain in the routing table until they manually removed.</li>
            <li>When changes to the network occur, static entries must be modified, added, or removed.</li>
            <li>Static routing works well in smaller networks.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Dynamic</td>
        <td class="content">
          Maintaining static only routing in a large network with multiple routers would be very difficult, especially when there
          are multiple network paths that an IP packet can take to get to its destination. Routers can dynamically learn about
          networks by sharing routing information with other routers.
          <ul>
            <li>Dynamic routing is implemented by enabling a routing protocol.</li>
            <li>A routing protocol adds dynamic entries to the routing table.</li>
            <li>If multiple paths to a network are available, routing protocols define:
              <ul>
                <li>The algorithm used to calculate a metric.</li>
                <li>How routers communicate with each other to share network path information.</li>
              </ul>
            </li>
            <li>Routing protocols use metric information to insert the best hop into the routing table when multiple paths are
            available.</li>
          </ul>
          <p>If needed, you can add static routes to supplement dynamic routing to identify networks that are not learned about
          through any routing protocol.</p>
        </td>
      </tr>
    </tbody>
  </table>

  <h3 style="color:#F96302">Interior and Exterior Routing</h3>

  <p>Dynamic routing protocols can be classified by their use, either for interior routing or exterior routing.</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Routing Use</td>
        <td class="contentheader">Description</td>
      </tr>
      <tr>
        <td class="centered">Interior</td>
        <td class="content">
          Interior routing is done within an autonomous system (AS). An autonomous system is a private network that is somewhat
          independent of the internet. The only thing that is shared is the link to the internet.
          <p>With interior routers:</p>
          <ul>
            <li>You own and control the routers.</li>
            <li>You determine where the routers are located.
              <ul>
                <li>You control the logical topology.</li>
                <li>You control the physical topology.</li>
              </ul>
            </li>
            <li>You control the interfaces that connect the routers to your network.</li>
            <li>You determine which interior routing protocols are enabled.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Exterior</td>
        <td class="content">
          Exterior routing is done between autonomous systems. Organizations that connect their private network to the internet are
          assigned a unique autonomous system number, or ASN.
          <ul>
            <li>Exterior routing is the routing performed by the so-called internet backbone.</li>
            <li>In most organizations, exterior routing will be limited to a single router that connects the organizations network
            to the internet via an ISP.
              <ul>
                <li>This router is often called a border router or an edge router.</li>
              </ul>
            </li>
            <li>Larger organizations or organizations with a critical mission may have multiple ISPs that give them redundant
            internet connectivity. In this case, the edge router or routers must run an exterior routing protocol.</li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
</div></div>



| Protocol                                           | Type | Category        | Description |
| -------------------------------------------------- | ---- | --------------- | ---|
| Routing Information Protocol (RIP)                 | IGP  | Distance Vector | RIP is a distance vector routing protocol used for routing within an autonomous system (such as an IGP). RIP uses hop count as the metric. RIP network size is limited to a maximum of 15 hops between any two networks. A network with a hop count of 16 indicates an unreachable network. RIP v1 is a classful protocol; RIP v2 is a classless protocol. RIP is best suited for small private networks. |
| Enhanced Interior Gateway Routing Protocol (EIGRP) | IGP  | Hybrid          | EIGRP is a hybrid routing protocol developed by Cisco for routing within an AS. EIGRP uses a composite number for the metric, which indicates bandwidth and delay for a link. The higher the bandwidth, the lower the metric. EIGRP is a classless protocol. EIGRP is best suited for medium to large private networks. |
| Open Shortest Path First (OSPF)                    | IGP  | Link State      | OSPF is a link state routing protocol used for routing within an AS. OSPF uses relative link cost for the metric. OSPF is a classless protocol. OSPF divides a large network into areas. Each autonomous system requires an area 0 that identifies the network backbone. All areas are connected to area 0, either directly or indirectly through another area. Routes between areas must pass through area 0. Internal routers share routes within an area; area border routers share routes between areas; autonomous system boundary routers share routes outside of the AS. A router is the boundary between one area and another area. OSPF is best suited for large private networks. |
| Intermediate System to Intermediate System (IS-IS) | IGP  | Link State      | IS-IS is a link-state routing protocol used for routing within an AS. IS-IS uses relative link cost for the metric. IS-IS is a classless protocol. The original IS-IS protocol was not used for routing IP packets; use integrated IS-IS to include IP routing support. IS-IS divides a large network into areas. There is no area 0 requirement, and IS-IS provides greater flexibility for creating and connecting areas than OSPF . L1 routers share routes within an area. L2 routers share routes between areas. An L1/L2 router can share routes with both L1 and L2 routers. A network link is the boundary between one area and another area. IS-IS is best suited for large private networks; it supports larger networks than OSPF. IS-IS is typically used within an ISP and easily supports IPv6 routing. |
| Border Gateway Protocol (BGP)                      | EGP  | Hybrid          | BGP is an advanced distance vector protocol (also called a path vector protocol). BGP is an exterior gateway protocol (EGP) used for routing between autonomous systems. BGP uses paths, rules, and policies instead of a metric for making routing decisions. BGP is a classless protocol. Internal BGP (iBGP) is used within an autonomous system; External BGP (eBGP) is used between autonomous systems. BGP is the protocol used on the internet; ISPs use BGP to identify routes between autonomous systems. Very large networks can use BGP internally, but typically share routes on the internet only if the AS has two (or more) connections to the internet through different ISPs.                                                                                                                        |

<div class="TextViewer-container"><div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>What network link characteristics are used by routing protocols when computing a metric value or cost?</li>
      <li>How does a distance vector routing protocol differ from a link state routing protocol?</li>
      <li>How are routing paths shared by distance vector routing protocols?</li>
      <li>How are routing paths shared by link state routing protocols?</li>
      <li>What is a hybrid routing protocol?</li>
      <li>How is administrative distance used to select a best path?</li>
      <li>What is the difference between RIP and RIPv2? Why is this important in today's networks?</li>
      <li>Which routing protocol is typically used within an ISP? Which protocol is used on the internet?</li>
      <li>Which routing protocols divide an autonomous system into areas?</li>
      <li>How does IS-IS differ from OSPF?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure a router with static routes.</li>
      <li>Enable OSPF routing.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Hop Count</td>
      <td class="content">The distance between networks can be measured in hop 
		counts, or the number times a router forwards an IP packet from one 
		network to another. For a directly connected link, the hop count is zero.</td>
    </tr>
    <tr>
      <td class="centered">Bandwidth</td>
      <td class="content">Network bandwidth measures the capacity of a link. If bandwidth is a factor in the cost, a link with a
      lower capacity link will have a higher cost than a link with high 
		bandwidth.</td>
    </tr>
    <tr>
      <td class="centered">Throughput</td>
      <td class="content">Although the advertised bandwidth is the maximum capacity of a link, its actual throughput will be less
      due to latency and other network overhead. If used in the cost calculation, larger throughput will contribute to a lower
      cost.</td>
    </tr>
    <tr>
      <td class="centered">Link Utilization</td>
      <td class="content">Link utilization is the percentage of a network's bandwidth that is currently being consumed by
      network traffic. If utilization is used, the cost will be less for links with low utilization.</td>
    </tr>
    <tr>
      <td class="centered">Load</td>
      <td class="content">The load on a router refers to the amount of computational work that it performs. If load is a factor in
      the cost, links for routers that are performing under heavy load will have a higher cost.</td>
    </tr>
    <tr>
      <td class="centered">MTU</td>
      <td class="content">The maximum transmission unit (MTU) setting on a router determines the maximum payload size for a frame.
      While this characteristic is not usually included in a metric, it is sometimes used as a tie-breaker when two links or paths
      have the same cost.</td>
    </tr>
    <tr>
      <td class="centered">Packet Loss</td>
      <td class="content">Packet loss occurs when IP packets fail to reach their destination. If it is used in calculating cost, a
      link that experiences greater packet loss will have a higher cost.</td>
    </tr>
    <tr>
      <td class="centered">Latency</td>
      <td class="content">Latency is the delay in transmissions over the path. If latency is used in the cost, a path with higher
      latency has a higher cost.</td>
    </tr>
    <tr>
      <td class="centered">Reliability</td>
      <td class="content">Reliability is measured by how often the path is down. 
		If it is used in cost calculations, a highly reliable path has a lower cost.</td>
    </tr>
  </tbody></table>
</div></div>
<div class="TextViewer-container"><div id="TextViewer-root" class="TextViewer-root">
  <p>Routers use a routing protocol to assign a metric to a network path and exchange information about paths with other
  routers. In this lesson, you will learn about:</p>

  <ul>
    <li>Routing metrics</li>
    <li>Routing protocol categories</li>
    <li>Distance vector protocols</li>
    <li>Link state protocols</li>
    <li>Hybrid protocols</li>
    <li>Administrative distance</li>
    <li>Configure a static route</li>
  </ul>

  <h3 style="color:#F96302">Routing Metrics</h3>

  <p>If there are multiple paths to a distant network, a routing protocol will assign a metric to each directly connected network
  link. The metric value can be thought of as the cost of sending a packet over that link. The metric is used when determining the
  best path to a network.</p>

  <p>A routing protocol can use one or more of the following characteristics:</p>

  <table border="1">
    <tbody><tr class="header">
      <td class="centered">Characteristic</td>
      <td class="contentheader">Description</td>
    </tr>
    <tr>
      <td class="centered">Hop Count</td>
      <td class="content">The distance between networks can be measured in hop counts, or the number times a router forwards an IP
      packet from one network to another. For a directly connected link, the hop count will be zero.</td>
    </tr>
    <tr>
      <td class="centered">Bandwidth</td>
      <td class="content">Network bandwidth measures the capacity of a link. If bandwidth is a factor in the cost, a link with a
      lower capacity link will have a higher cost than a link with a high bandwidth link.</td>
    </tr>
    <tr>
      <td class="centered">Throughput</td>
      <td class="content">Although the advertised bandwidth is the maximum capacity of a link, its actual throughput will be less
      due to latency and other network overhead. If used in the cost calculation, larger throughput will contribute to a lower
      cost.</td>
    </tr>
    <tr>
      <td class="centered">Link Utilization</td>
      <td class="content">Link utilization is the percentage of a network's bandwidth that is currently being consumed by
      network traffic. If utilization is used, the cost will be less for links with low utilization.</td>
    </tr>
    <tr>
      <td class="centered">Load</td>
      <td class="content">The load on a router refers to the amount of computational work that it performs. If load is a factor in
      the cost, links for routers that are performing under heavy load will have a higher cost.</td>
    </tr>
    <tr>
      <td class="centered">MTU</td>
      <td class="content">The maximum transmission unit (MTU) setting on a router determines the maximum payload size for a frame.
      While this characteristic is not usually included in a metric, it is sometimes used as a tie-breaker when two links or paths
      have the same cost.</td>
    </tr>
    <tr>
      <td class="centered">Packet Loss</td>
      <td class="content">Packet loss occurs when IP packets fail to reach their destination. If 
		it is used in calculating cost, a link
      that experiences greater packet loss will have a higher cost.</td>
    </tr>
    <tr>
      <td class="centered">Latency</td>
      <td class="content">Latency is the delay in transmissions over the path. If latency is used in the cost, a path with higher
      latency will have a higher cost.</td>
    </tr>
    <tr>
      <td class="centered">Reliability</td>
      <td class="content">Reliability is measured by how often the path is down. If 
		it is used in cost calculations, a highly reliable
      path will have a lower cost.</td>
    </tr>
  </tbody></table>

  <h3 style="color:#F96302">Routing Protocol Categories</h3>

  <p>There are two primary categories of gateway protocols, distance vector protocols and link state protocols. A third category is
  a combination of these two, hybrid protocols. There is only one popular exterior routing protocol, and it is a hybrid
  protocol.</p>

  <p>The difference in these categories of routing protocols is:</p>

  <ul>
    <li>How metric values are calculated</li>
    <li>How path information is shared between routers</li>
  </ul>

  <h3 style="color:#F96302">Distance Vector Routing Protocols</h3>

  <p>Distance vector routing protocols:</p>

  <ul>
    <li>Set a metric value or cost based on how far away a network is.
      <ul>
        <li>Are generally measured by hop count.</li>
        <li>May measure distance by delay, packets lost, or something similar.</li>
      </ul>
    </li>
    <li>Set a direction that is associated with the distance.
      <ul>
        <li>Direction refers to the network interface that is used to forward the IP packet to the distant network.</li>
      </ul>
    </li>
  </ul>

  <p>When using a distance vector protocol, a router:</p>

  <ul>
    <li>Will only share information with its direct neighbors (the next hop routers).</li>
    <li>Will share all route information that it knows about.
      <ul>
        <li>Directly connected routes</li>
        <li>Routes learned from its direct neighbors</li>
      </ul>
    </li>
    <li>Will send route information at a regularly scheduled time.</li>
  </ul>

  <p>Convergence occurs when all routers share a consistent view of the network. Each router will used converged path information
  to insert next hop information for each learned path into the routing table. It does this by choosing the route with the lowest
  metric.</p>

  <h3 style="color:#F96302">Link State Routing Protocols</h3>

  <ol>
	<li>Link state protocols are also known as shortest path first protocols. The following is the general process employed by a
  router that uses link state protocols for finding best hop information.</li>
	<li>The router examines its directly connected network links and assigns a metric value.
      <ul>
		<li>The metric value is based on the status and connection type of the link.</li>
		<li>The metric value may also include other factors, such as bandwidth and delay.</li>
	</ul></li>
	<li>The router determines the neighbor routers that are connected by each direct network link.</li>
	<li>The router builds a link-state packet (LSP) that contains a list of its neighbors and the metric value of the link to that
    neighbor.</li>
	<li>Through a process called flooding, the router sends the LSP to its neighbor routers.</li>
	<li>Neighboring routers, in turn, sends the LSP to its neighbors, and so on.
	<ul>
		<li>To eliminate looping, each router forwards the packet to every neighbor except the one it received the packet
        from.</li>
		<li>A smart flooding algorithm prevents looping when there are circular routing paths.</li>
	</ul></li>
	<li>Using converged route information, the router constructs a complete map of the routing topology.</li>
	<li>From this map, the router will calculate the best path to each destination network.
      <ul>
		<li>Best path is determined using Dijkstras’s algorithm, which calculates the shortest path first.</li>
	</ul></li>
	<li>Using the link-state protocol, the router uses the best path information to insert next hop information for each network
    path into the routing table.</li>
	</ol>
	<h3 style="color:#F96302">Administrative Distance</h3>

  <p>When more than one protocol is enabled on a router, each protocol is given an administrative distance. When 
	the best
  path is being determined, protocols with a lower administrative distance are chosen over those with a higher administrative distance.</p>

  <p>Most routers have a default administrative distance assigned to each routing protocol.</p>

  <table border="1">
    <tbody><tr class="header">
      <td class="contentheader">Source of the Route</td>
      <td class="contentheader">Default Administrative Distance</td>
    </tr>
    <tr>
      <td class="content">Connected interface or static route to an interface</td>
      <td class="content">0</td>
    </tr>
    <tr>
      <td class="content">Static route to an IP address</td>
      <td class="content">1</td>
    </tr>
    <tr>
      <td class="content">EIGRP summary</td>
      <td class="content">5</td>
    </tr>
    <tr>
      <td class="content">BGP external</td>
      <td class="content">20</td>
    </tr>
    <tr>
      <td class="content">EIGRP internal</td>
      <td class="content">90</td>
    </tr>
    <tr>
      <td class="content">IGRP</td>
      <td class="content">100</td>
    </tr>
    <tr>
      <td class="content">OSPF</td>
      <td class="content">110</td>
    </tr>
    <tr>
      <td class="content">IS-IS</td>
      <td class="content">115</td>
    </tr>
    <tr>
      <td class="content">RIP</td>
      <td class="content">120</td>
    </tr>
    <tr>
      <td class="content">EIGRP external</td>
      <td class="content">170</td>
    </tr>
    <tr>
      <td class="content">BGP internal</td>
      <td class="content">200</td>
    </tr>
    <tr>
      <td class="content">Unknown source</td>
      <td class="content">255</td>
    </tr>
  </tbody></table>

  <h3 style="color:#F96302">Configure a Static Route</h3>

  <p>To configure a static route, enter the following commands at the prompt:</p>

  <p><span class="code">SFO&gt;<b>enable</b><br>
  SFO#<b>configure terminal</b><br>
  SFO(config)#<b>ip route <i>network_address</i> <i>subnet</i> <i>gateway</i></b><br>
  SFO(config)#<b>ip route 0.0.0.0 0.0.0.0 <i>gateway</i></b><br>
  SFO(config)#<b>exit</b><br>
  SFO#<b>copy run start</b><br></span></p>
</div></div>

## Routing config Lab solutions:

<div class="clsBoxText2">
  <p>Enter the following commands to configure the SFO static routes:</p>

  <ol>
    <li>In the diagram, select the SFO router.</li>
    <li>Press <b>Enter</b>.</li>
    <li>At the prompt, enter:
      <p><span class="code">SFO&gt;<b>enable</b><br>
      SFO#<b>configure terminal</b><br>
      SFO(config)#<b>ip route 10.0.0.0 255.0.0.0 172.17.12.98</b><br>
      SFO(config)#<b>ip route 0.0.0.0 0.0.0.0 160.12.99.1</b><br> </span></p><blockquote class="info">Make sure
    	to add a space between the 2 octets of zeros.</blockquote><br>
      SFO(config)#<b>exit</b><br>
      SFO#<b>copy run start</b><br><p></p>
    </li>
    <li>Press <b>Enter</b>.</li>
    <li>Press <b>Enter</b> to save your changes.</li>

  </ol>
</div>

<div class="clsBoxHeader2">Explanation</div><div class="clsBoxText2">
  <p>In this lab, your task is to complete the following:</p>

  <ul>
    <li>Configure the Salta router to share information about all directly connected routes with the Jujuy router.</li>
    <li>When you are finished, save your changes.</li>

  </ul>

  <p>When configuring OSPF, routers do not need to use the same process ID, but networks must be defined in the same area. When
  adding network statements, include the wildcard mask and the area number (in this case, area 0).</p>

  <p>Complete this lab as follows:</p>

  <ol>
    <li>Select <b>Salta</b>.</li>
    <li>Press <b>Enter</b>.</li>
    <li>At the prompt, enter:
      <blockquote>
        <span class="code">Salta&gt;<b>enable</b><br>
        Salta#<b>config t</b><br>
        Salta(config)#<b>router ospf 100</b><br>
        Salta(config-router)#<b>network 192.168.1.0 0.0.0.255 area 0</b><br>
        Salta(config-router)#<b>network 192.168.2.0 0.0.0.255 area 0</b><br>
        Salta(config-router)#<b>network 172.17.150.140 0.0.0.3 area 0</b></span>
      </blockquote>
    </li>
    <li>Press <b>Ctrl</b> + <b>Z</b>.</li>
    <li>Enter the following command at the prompt:
      <blockquote>
        <span class="code">Salta#<b>copy running-config startup-config</b></span>
      </blockquote>
    </li>
    <li>Press <b>Enter</b>.</li>
    <li>Press <b>Enter</b> to save your changes.</li>
  </ol>
</div>

<h2 style="color:#F96302">NAT</h2>

| Term |Definition |
| ---- | ---- |
| Network Address Translation (NAT) | NAT translates private addresses to the public address of the NAT router. This allows you to connect a private network to the internet without obtaining registered (public) addresses for every host. |
| Port Address Translation (PAT)    | Technically speaking, NAT translates one address to another. Port address translation (PAT) associates a port number with the translated address.                                                      |

<div class="TextViewer-container"><div id="TextViewer-root" class="TextViewer-root">
  <p>Network address translation (NAT) allows you to connect a private network 
	to the internet without obtaining registered addresses for every host. This 
	lesson covers:</p>

  <ul>
    <li>How NAT works</li>
    <li>Implementing NAT</li>
    <li>Reserved private IP addresses</li>
  </ul>

  <h3 style="color:#F96302">How NAT Works</h3>

  <p>NAT works by translating private addresses to the public address of the NAT 
	router.</p>

  <ul>
    <li>Hosts on the private network share the IP address of the NAT router or a pool of addresses assigned for the network.</li>
    <li>The NAT router maps port numbers to private IP addresses. Responses to internet requests include the port number appended
    by the NAT router. This allows the NAT router to forward responses back to the correct private host.</li>
    <li>Technically speaking, NAT translates one address to another. Port address translation (PAT) associates a port number with
    the translated address.
      <ul>
        <li>With only NAT, you would need a public address for each private host. NAT associates a single public address with a
        single private address.</li>
        <li>PAT allows multiple private hosts to share a single public address. Each private host is associated with a unique port
        number on the NAT router.</li>
        <li>Because virtually all NAT routers perform PAT, you normally use PAT, and not just NAT, when you use a NAT router.
        (NAT is usually synonymous with PAT.)</li>
      </ul>
    </li>
  </ul>

  <h3 style="color:#F96302">Implementing NAT</h3>

  <p>When you implement NAT, be aware of the following:</p>

  <ul>
    <li>NAT supports a limit of 5,000 concurrent connections.</li>
    <li>NAT provides some security for the private network because it translates or hides private addresses.</li>
    <li>A NAT router can act as a limited-function DHCP server, assigning addresses to private hosts.</li>
    <li>A NAT router can forward DNS requests to the internet.</li>
  </ul>

  <p>The following table describes three types of NAT implementation. </p>

| Type                   | Description |
| --- | --- |
| **Dynamic NAT** | Dynamic NAT automatically maps internal IP addresses with a dynamic port assignment. On the NAT device, the internal device is identified by the public IP address and the dynamic port number. Dynamic NAT allows internal (private) hosts to contact external (public) hosts, but not vice versa—external hosts cannot initiate communications with internal hosts. This implementation is also sometimes called many-to-one NAT because many internal private IP address are mapped to one public IP address on the NAT router.  |
| **Static NAT (SNAT)** | Static NAT maps a single private IP address to a single public IP address on the NAT router. Static NAT is used to take a server on the private network (such as a web server) and make it available on the internet. Using a static mapping allows external hosts to contact internal hosts—external hosts contact the internal server using the public IP address and the static port. This implementation is called one-to-one NAT because one private IP address is mapped to one public IP address. In addition to static NAT, the term SNAT also means source NAT, stateful NAT, and secure NAT. Although the terms vary, the function is the same. One commonly used implementation of static NAT is called port forwarding. Port forwarding allows incoming traffic addressed to a specific port to move through the firewall and be transparently forwarded to a specific host on the private network. Inbound requests are addressed to the port used by the internal service on the router's public IP address (such as port 80 for a web server). This is often called the public port. Port forwarding associates the inbound port number with the IP address and port of a host on the private network. This port is often called the private port. Based on the public port number, incoming traffic is redirected to the private IP address and port of the destination host on the internal network. Port forwarding is also called destination network address translation, or DNAT. |
| **Dynamic and Static NAT** | Dynamic and static NAT, where two IP addresses are given to the public NAT interface (one for dynamic NAT and one for static NAT), allows traffic to flow in both directions. |

<h3 style="color:#F96302">Reserved Private IP Addresses</h3>

<p>When connecting a private network to the internet through NAT, IP addresses on the private network are commonly those reserved
by the Internet Assigned Numbers Authority (IANA) for that purpose. These address ranges are guaranteed not to be used on the
internet and do not need to be registered. The private IPv4 address ranges are:</p>

<ul>
    <li>10.0.0.1 to 10.255.255.254</li>
    <li>172.16.0.1 to 172.31.255.254</li>
    <li>192.168.0.1 to 192.168.255.254</li>
</ul>
</div>
</div>

<div class="TextViewer-container"><div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>How is it possible for all hosts on a subnet to be configured with the wrong default gateway address?</li>
      <li>What is the format for the default route entry in a routing table? What purpose does the default route serve?</li>
      <li>What are the symptoms of a routing loop? How can you identify a routing loop?</li>
      <li>Why might you escalate routing problems that you observe?</li>
      <li>How can proxy ARP settings appear as routing problems?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Troubleshoot routing.</li>
      <li>Find path information.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Neighbor Discovery<br>
      (ND)</td>
      <td class="content">ND enables routers on the same link to advertise their existence to neighboring routers and to learn
      about the existence of their neighbors. Routers use ND messages to identify the link-layer addresses of neighboring devices
      that are directly connected to the router.</td>
    </tr>
    <tr>
      <td class="centered">Black Hole Router</td>
      <td class="content">A black hole router is a router that drops packets if the size of the packet exceeds the Maximum
      Transmission Unit (MTU) size it can support. It is called a black hole 
		because the router does not send an error message to the sending host 
		when it drops an oversize packet. In essence, the packet enters a 
		network "black hole."</td>
    </tr>
    <tr>
      <td class="centered">Routing loop</td>
      <td class="content">A routing loop occurs when data is being passed back and forth between routers in the path instead of
      forwarding it to the destination network.</td>
    </tr>
  </tbody></table>
</div></div>

<div class="TextViewer-container"><div id="TextViewer-root" class="TextViewer-root">
  <p>A general routing problem symptom is the inability to access hosts on a specific network or any remote network. In this lesson,
  you will learn how to troubleshoot a few routing problems:</p>

  <ul>
    <li>Can't access hosts outside the local subnet.</li>

    <li>Can't communicate with any host on a specific network.</li>

    <li>Can't access the internet.</li>

    <li>Remote clients can't access network resources.</li>

  </ul>

<h3 style="color:#F96302">Troubleshooting Strategies</h3>

<p>The following table presents a general troubleshooting strategy for each of 
these routing issues.</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered">Problem</td>
        <td class="contentheader">Troubleshooting Strategy</td>
      </tr>
      <tr>
        <td class="centered">Can't access hosts outside the local subnet</td>
        <td class="content">
          If one or more hosts can communicate only with hosts on the local subnet, the problem is likely with the default gateway
          configuration.
          <ul>
            <li>If a single host is having problems, check the default gateway setting on that host.</li>
            <li>If multiple hosts are having problems, check the default gateway setting and verify that the DHCP server is
            configured to deliver the correct default gateway address.</li>
            <li>If all hosts have the same problem and the default gateway setting is correct, verify that the default gateway
            server is up and configured for routing.</li>
          </ul>
          <p>This issue could also be caused by problems with the neighbor discovery (ND) protocol.</p>
          <ul>
            <li>Routers on the same link use the ND protocol to advertise their existence to neighboring routers and to learn about
            the existence of their neighbors.</li>
            <li>Routers process ND messages to identify the link layer addresses of neighboring devices that are directly connected
            to the router.</li>
            <li>Routers use the ND protocol to periodically send and receive small hello packets to and from neighboring routers.
            If hello packets are not received from a particular router, it is
    		assumed that the router is not functioning. </li>
          </ul>
          <p>Issues with the ND protocol can occur when a large subnet is used for point-to-point links between routers, especially
          when IPv6 is used. By convention, a /64 prefix is used on each subnet when implementing IPv6, allowing for a very large
          number of hosts on the subnet. If you use a standard /64 prefix on the link subnet, the ND protocol will try to perform
          address resolution for all possible hosts on the subnet. When this happens, newly connected devices may not be recognized
          by other routers for a long period of time.</p>
          <p>A point-to-point link between routers is composed of only two interfaces, one on each end of the link. Therefore, the
          link subnet needs only to support a maximum of two hosts. As a recommended best practice, use a very small subnet for the
          point-to-point link between routers to reduce ND traffic. The recommendation is to use 127-bit (/127) prefixes on these
          links instead of the conventional 64-bit prefix.</p>
        </td>
      </tr>
      <tr>
        <td class="centered">Can't communicate with any host on a specific network</td>
        <td class="content">
          If hosts are unable to contact hosts on a specific subnet but they can communicate with other subnets, try the
          following:
          <ol>
    		<li>Verify that the router connected to the subnet is up.</li>
    		<li>Use the <b>route</b> command on the default gateway of the local subnet and verify that the router has a route to
            the remote subnet. If necessary, configure a routing protocol so that the route can be learned automatically or
            configure a static route.</li>
    		<li>Use <b>traceroute</b> to view the route taken to the destination network. Identify the last router in the path
    		and
            then troubleshoot routing at that point.</li>
    		<li>Check for routing loops in the path to the destination network. A routing loop is caused by a misconfiguration in
            the routers along the path, causing data to be sent back along the same path rather than forwarded to the destination.
            Routing loops are indicated by:
    		<ul>
    			<li>Routing table entries that appear and then disappear (called
    			<i>route flapping</i>), often at regular intervals
                (such as every minute).</li>
    			<li>Routing table entries where the next hop router address oscillates (switches) between two or more different
                routers.
                  <blockquote class="info">Routing loops are displayed in a <b>traceroute</b> output and shows the same sequence of routers being
                    repeated.
                  </blockquote></li>
    		</ul></li>
    		<li>Check for black hole routers. A
             black hole router causes the ping utility to send an ICMP echo packet that has the IP "Do not Fragment" or DF
                bit set.</li>
    			<li><b>-l</b> sets the buffer (or payload) size of the ICMP echo packet. Specify this size by typing a number after
                the <b>-l</b> parameter.</li>
    		The ping test will provide you with helpful information:
    		<ul>
    			<li>If the MTU of every segment of a routed connection is at least the MTU size, the packet is successfully
                returned.</li>
    			<li>If there are intermediate segments that have smaller MTUs, and the routers return the appropriate ICMP destination unreachable packet, the ping utility displays the message, "Packet needs to be
                fragmented but DF set."</li>
    			<li>If there are intermediate segments that have smaller MTUs and the routers do not return the appropriate ICMP
                "destination unreachable" packet, the ping utility displays the message, "Request timed
                out."</li>
    		</ul>
    		</ol>
        </td>
      </tr>
      <tr>
        <td class="centered">Can't access the internet</td>
        <td class="content">
          If hosts are able to reach all internal networks but can't access the
    		internet, try the following:
          <ul>
            <li>Verify that the internet connection is up.</li>
            <li>Check for a default route on the router connected to the internet. A default route is indicated by a network
            address of 0.0.0.0 with a mask of 0.0.0.0. The default route is used for packets that do not match any other entries in
            the routing table.</li>
          </ul>
          <blockquote class="info">
            Most routers that connect private networks to the internet do not know about specific networks and routes on the
            internet. Additionally, most routers do not share routes for private subnets with
    		internet routers. A router is
            configured with a single default route that is used for all internet traffic, and a router at the ISP is responsible
            for sharing a single route for your private network with other internet routers.
          </blockquote>
        </td>
      </tr>
      <tr>
        <td class="centered">Remote clients can't access network resources</td>
        <td class="content">
          If you have remote access clients who can establish a connection to the remote access server but can't connect to
          other resources on the private network, check the following:
          <ul>
            <li>If remote clients are being assigned IP addresses on the same subnet as the private network, make sure that proxy
            ARP is enabled on the LAN interface of the remote access server. Proxy ARP makes it appear as if the remote clients are
            connected to the same network segment.</li>
            <li>If remote clients are being assigned IP addresses on a different subnet than the private network, make sure the
            remote access server is configured to route packets between the remote clients and the private network.</li>
          </ul>
        </td>
      </tr>
    </tbody>

  </table>
</div></div>
<br/>

# Chapter 8 Firewalls
###### [Back to top](#Network-Security-and-Data-Communications)
</br>
<div>
  <p>As you study this section, answer the following questions:</p>
  <div>
    <ul>
      <li>How does a packet filtering firewall differ from a circuit-level gateway?</li>
      <li>Why is a packet filtering firewall a stateless device?</li>
      <li>What types of filter criteria can an application layer gateway use for filtering?</li>
      <li>Which security device might you choose to restrict access by user account?</li>
      <li>What is the difference between a proxy and a reverse proxy?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Configure a host firewall.</li>
      <li>Configure Linux iptables.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Firewall</td>
      <td class="content">A firewall is a software- or hardware-based network security system that allows or denies network traffic
      according to a set of rules.</td>
    </tr>
    <tr>
      <td class="centered">Access Control List (ACL)</td>
      <td class="content">Filtering rules firewalls use to identify which 
		traffic to allow and which traffic to block. </td>
    </tr>
    <tr>
      <td class="centered">Network Ports</td>
      <td class="content">Network ports are logical connections provided by the TCP or UDP protocols at the Transport layer. They
      are used by protocols in the upper layers of the OSI model. The TCP/IP protocol stack uses port numbers to determine which
      protocol incoming traffic should be directed to.</td>
    </tr>
    <tr>
      <td class="centered">iptables</td>
      <td class="content">iptables is a command line firewall utility for Linux 
		operation systems that uses three different policy chains to allow or 
		block network traffic.</td>
    </tr>
  </tbody></table>
</div>
</div>

## Firewall Facts
<div id="TextViewer-root" class="TextViewer-root">
  <p>A <i>firewall</i> is a software- or hardware-based network security system 
	that allows or denies network traffic according to a set of rules.</p>

  <h3 style="color:#F96302">Firewall Types</h3>

  <p>You can categorize firewalls by their location on the network:</p>

  <ul>
    <li>A network-based firewall is installed on the edge of a private network 
	or network segment.
      <ul>
        <li>Most network-based firewalls are considered hardware firewalls even 
		though they use a combination of hardware and software to protect the 
		network from internet attacks.</li>
        <li>Network-based firewalls are more expensive and require more 
		configuration than other types of firewalls, but they are much more 
		robust and secure.</li>
      </ul>
    </li>
  </ul>

  <p>A host-based firewall is installed on a single computer in a network.</p>

  <ul>
    <li>Almost all host-based firewalls are software firewalls.</li>

    <li>A host-based firewall can protect a computer when no network-based 
	firewall exists (in other words, when connected to a public network).</li>

    <li>Host-based firewalls are less expensive and easier to use than 
	network-based firewalls, but they don't offer the same level of protection 
	or customization.

      <blockquote class="info">
        You can use a host-based firewall in addition to a network-based 
		firewall to provide multiple layers of protection.
      </blockquote>
    </li>
  </ul>

  <h3 style="color:#F96302">Access Control Lists</h3>

  <p>Firewalls use filtering rules, which are sometimes called access control 
	lists (ACLs), to identify allowed and blocked traffic. A rule identifies 
	specific characteristics:</p>

  <ul>
    <li>The interface the rule applies to</li>

    <li>The direction of traffic (inbound or outbound)</li>

    <li>Packet information such as the source IP address, destination IP 
	address, or port number</li>

    <li>The action to take when the traffic matches the filter criteria</li>
  </ul>

  <blockquote class="info">
    Each ACL has an implicit deny specification. This is a line at the end of 
	the ACL stating that packets that don't match any defined rules are dropped.
  </blockquote>

  <ul>
    <li>Firewalls do not offer protection against all attacks (such as email 
	spoofing attacks).</li>
  </ul>

  <p>The following table describes firewall types:</p>

  <table>
    <tbody>
      <tr class="header">
        <td class="centered">Firewall Type</td>
        <td class="contentheader">Characteristics</td>
      </tr>
      <tr>
        <td class="centered">Packet Filtering Firewall</td>
        <td class="contentheader">
          A packet filtering firewall allows and blocks network traffic by 
			examining information in the IP packet heade,r such as source and 
			destination addresses, ports, and service protocols. A packet 
			filtering firewall:
          <ul>
            <li>Uses ACLs or filter rules to control traffic.</li>
            <li>Operates at OSI Layer 3 (Network layer).</li>
            <li>Offers high performance because it examines only the address 
			information in the packet header.</li>
            <li>Implements features that are included in most routers.</li>
            <li>Is a popular solution because it is easy to implement and 
			maintain, has a minimal impact on system performance, and is fairly 
			inexpensive.</li>
          </ul>
          <p>A packet filtering firewall is considered a stateless firewall 
			because it examines each packet and uses rules to accept or reject 
			it without considering whether the packet is part of a valid and 
			active session.</p>
        </td>
      </tr>
      <tr>
        <td class="centered">Circuit-Level Gateway</td>
        <td class="contentheader">
          A circuit-level gateway makes decisions about which traffic to allow 
			based on virtual circuits or sessions. A circuit-level gateway:
          <ul>
            <li>Operates at OSI Layer 5 (Session layer).</li>
            <li>Keeps a table of known connections and sessions. Packets 
			directed to known sessions are accepted.</li>
            <li>Verifies that packets are properly sequenced.</li>
            <li>Ensures that the TCP three-way handshake process occurs only 
			when appropriate.</li>
            <li>Does not filter packets. Instead, it allows or denies sessions.</li>
          </ul>
          <p>A circuit-level gateway is considered a stateful firewall because 
			it keeps track of a session's state A circuit-level gateway can 
			filter traffic that uses dynamic ports because the firewall matches 
			the session information for filtering, not the port numbers. In 
			general, circuit-level gateways are slower than packet filtering 
			firewalls. However, if only the session state is used for filtering, 
			a circuit-level gateway can be faster after the initial session 
			information has been identified.</p>
        </td>
      </tr>
      <tr>
        <td class="centered">Application-Layer Firewall</td>
        <td class="contentheader">
          An application-layer firewall is capable of filtering by information 
			contained within a packet's data portion. An application-layer 
			firewall:
          <ul>
            <li>Examines the entirety of the transferred content (not just 
			individual packets).</li>
            <li>Operates at OSI Layer 7 (Application layer).</li>
            <li>Understands, or interfaces with, the application-layer protocol.</li>
            <li>Filters content by user, group, and data (for example, URLs 
			within an HTTP request).</li>
            <li>Is the slowest form of firewall because entire messages are 
			reassembled at the Application layer.</li>
          </ul>
          <p>One example of an application-layer firewall is a proxy server. A 
			proxy server is a device that stands as an intermediary between a 
			secure private network and the public. Proxies can be configured to:</p>
          <ul>
            <li>Control both inbound and outbound traffic.</li>
            <li>Increase performance by caching frequently accessed content. 
			Content is retrieved from the proxy cache instead of the original 
			server.</li>
            <li>Filter content and restrict access depending on the user or 
			specific website.</li>
            <li>Shield or hide a private network.</li>
          </ul>
          <p>There are two different types of proxy servers:</p>
          <ul>
            <li>A forward proxy server handles requests from inside a private 
			network out to the internet.</li>
            <li>A reverse proxy server handles requests from the internet to a 
			server located inside a private network. A reverse proxy can perform 
			load balancing, authentication, and caching.
              <blockquote class="info">
                Often, reverse proxies work transparently, meaning that clients 
				requesting specific resources don't know they are using a 
				reverse proxy to access a server.
              </blockquote>
            </li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Unified Threat Management (UTM) Device</td>
        <td class="contentheader">
          A unified threat management device combines multiple security features 
			into a single network appliance. A single UTM device can provide 
			several security features:
          <ul>
            <li>Firewall</li>
            <li>VPN</li>
            <li>Ant-spam</li>
            <li>Antivirus</li>
            <li>Load balancing</li>
          </ul>
          <p>By combining several services into one appliance, UTM devices make 
			managing network security much easier. However, they also introduce 
			a single point of failure—if the UTM fails, network security is 
			lost. Additionally, UTM devices aren't as robust as other devices 
			made for a specific use. Because of this, UTM devices are best 
			suited for:</p>
          <ul>
            <li>Offices where space limits don't allow for multiple security 
			appliances.</li>
            <li>Satellite offices that need to be managed remotely. 
			Configuration changes need to be made on only one device rather than 
			multiple devices.</li>
            <li>Smaller businesses that wouldn't benefit from the robust 
			features provided by specific security appliances.</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="centered">Next Generation Firewall (NGFW)</td>
        <td class="contentheader">
          A Next-Generation Firewall (NGFW) combines a traditional firewall with 
			other network device filtering functionalities like an application 
			firewall. An NGFW:
          <ul>
            <li>Is application-aware</li>
            <li>Tracks the state of traffic based on layers 2 through 7</li>
            <li>Utilizes an intrusion protection system (IPS)</li>
            <li>Tracks the identity of the local traffic device and user ( LDAP, 
			RADIUS, Active Directory)</li>
            <li>Can be used in bridged and routed modes</li>
            <li>Utilizes external intelligence sources</li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
  <p>A common method for using firewalls is to define various network zones. 
	Each zone identifies a collection of users who have similar access needs. 
	Firewalls are configured at the edge of these zones to filter incoming and 
	outbound traffic. For example, you can define a zone that includes all hosts 
	on your private network protected from the internet, and you can define 
	another zone within your network for controlled access to specific servers 
	that hold sensitive information.</p>
</div>

## Common Network Ports
<div id="TextViewer-root" class="TextViewer-root">
  <p><i>Network ports</i> are logical connections provided by the TCP or UDP protocols at the Transport layer. They are used by protocols
  in the upper layers of the OSI model. The TCP/IP protocol stack uses port numbers to determine which protocol incoming traffic
  should be directed to. Ports:</p>

  <ul>
    <li>Allow a single host with a single IP address to run network services. Each port number identifies a distinct service.</li>

    <li>Can have over 65,000 ports per IP address.</li>

    <li>Are regulated by the internet Corporation for Assigned Names and Numbers (ICANN).</li>
  </ul>

  <p>ICANN categorizes ports as follows:</p>

  <ul>
    <li>Well known ports range from 0 to 1023 and are assigned to common protocols and services.</li>

    <li>Registered ports range from 1024 to 49151 and are assigned to a specific service by ICANN.</li>

    <li>Dynamic (also called private or high) ports range from 49152 to 65535 and can be used by any service
    on an ad hoc basis. Ports are assigned when a session is established, and ports are released when the session ends.</li>
  </ul>

  <p>The following table lists the well-known ports that correspond to common internet services:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="centered" align="center">Port(s)</td>
        <td class="contentheader">Service</td>
      </tr>
      <tr>
        <td class="centered" align="center">20 TCP and UDP<br>
        21 TCP and UDP</td>
        <td class="content">File Transfer Protocol (FTP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">22 TCP and UDP</td>
        <td class="content">Secure Shell (SSH)</td>
      </tr>
      <tr>
        <td class="centered" align="center">22 TCP and UDP</td>
        <td class="content">SSH File Transfer Protocol (also known as Secure File Transfer Protocol or SFTP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">23 TCP</td>
        <td class="content">Telnet</td>
      </tr>
      <tr>
        <td class="centered" align="center">25 TCP and UDP</td>
        <td class="content">Simple Mail Transfer Protocol (SMTP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">53 TCP and UDP</td>
        <td class="content">Domain Name Server (DNS)</td>
      </tr>
      <tr>
        <td class="centered" align="center">67 TCP and UDP<br>
        68 TCP and UDP</td>
        <td class="content">Dynamic Host Configuration Protocol (DHCP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">69 TCP and UDP</td>
        <td class="content">Trivial File Transfer Protocol (TFTP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">80 TCP and UDP</td>
        <td class="content">Hypertext Transfer Protocol (HTTP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">110 TCP</td>
        <td class="content">Post Office Protocol (POP3)</td>
      </tr>
      <tr>
        <td class="centered" align="center">119 TCP</td>
        <td class="content">Network News Transport Protocol (NNTP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">123 TCP and UDP</td>
        <td class="content">Network Time Protocol (NTP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">137 TCP and UDP<br>
        138 TCP and UDP<br>
        139 TCP and UDP</td>
        <td class="content">NetBIOS Name Service<br>
        NetBIOS Datagram Service<br>
        NetBIOS Session Service</td>
      </tr>
      <tr>
        <td class="centered" align="center">143 TCP</td>
        <td class="content">internet Message Access Protocol (IMAP4)</td>
      </tr>
      <tr>
        <td class="centered" align="center">161 UDP<br>
        162 TCP and UDP</td>
        <td class="content">Simple Network Management Protocol (SNMP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">389 TCP and UDP</td>
        <td class="content">Lightweight Directory Access Protocol (LDAP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">443 TCP and UDP</td>
        <td class="content">HTTP over Secure Sockets Layer (HTTPS)</td>
      </tr>
      <tr>
        <td class="centered" align="center">445 TCP</td>
        <td class="content">Microsoft Server Message Block (SMB) File Sharing</td>
      </tr>
      <tr>
        <td class="centered" align="center">636 TCP and UDP</td>
        <td class="content">Lightweight Directory Access Protocol over TLS/SSL (LDAPS)</td>
      </tr>
      <tr>
        <td class="centered" align="center">1720 TCP</td>
        <td class="content">H.323 Call Signaling</td>
      </tr>
      <tr>
        <td class="centered" align="center">2427 UDP</td>
        <td class="content">Cisco Media Gateway Control Protocol (MGCP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">3389 TCP and UDP</td>
        <td class="content">Remote Desktop Protocol (RDP)</td>
      </tr>
      <tr>
        <td class="centered" align="center">5004 TCP and UDP<br>
        5005 TCP and UDP</td>
        <td class="content">Real-time Transport Protocol (RTP) Data<br>
        Real-time Transport Protocol (RTP) Control</td>
      </tr>
      <tr>
        <td class="centered" align="center">5060 TCP and UDP<br>
        5061 TCP</td>
        <td class="content">Session Initiation Protocol (SIP)<br>
        Session Initiation Protocol (SIP) over TLS</td>
      </tr>
    </tbody>
  </table>
  <blockquote class="info">
    To protect a server, ensure that only the necessary ports are open. For example, if the server is only used for email, shut
    down ports that correspond to FTP, DNS, HTTP, and other protocols.
  </blockquote>
</div>

## Linux IP Tables
<div id="TextViewer-root" class="TextViewer-root">
  <p>iptables is a command line firewall utility for Linux operation systems that uses three different policy chains to allow or
  block network traffic. When a connection is initiated to your system, iptables looks for a rule in its list to match it to. If it
  doesn't find one, it resorts to the default action in the tables.<br>
  <br>
  iptables almost always comes pre-installed on any Linux distribution. To update or install iptables, just retrieve the iptables
  package by entering the command: <code>sudo apt install iptables-services</code></p>

  <h3 style="color: #F96302">Chains</h3>

  <p>iptables uses three chains: input, forward, and output.</p>

  <table border="1">
    <tbody><tr class="header">
      <td class="centered">Chain</td>
      <td class="contentheader">Description</td>
    </tr>
    <tr>
      <td class="centered">Input</td>
      <td class="content">This chain controls the behavior for incoming connections. For example, if a user attempts to ping your
      system, iptables attempts to match the IP address and port to a rule in the input chain.</td>
    </tr>
    <tr>
      <td class="centered">Forward</td>
      <td class="content">This chain is used for incoming connections that aren't delivered locally. For example, if iptables
      are being used on a router, the traffic is not destined for the router, but the router will forward the traffic to the
      destination device.</td>
    </tr>
    <tr>
      <td class="centered">Output</td>
      <td class="content">This chain is used for outgoing connections. For example, if you try to ping testout.com, iptables checks
      its output chain to see what the rules are regarding ping and testout.com before allowing or denying the ping request.</td>
    </tr>
  </tbody></table>
  <h3 style="color:#F96302">Actions Performed</h3>
  <p>You need to decide what action you want the rules to perform. You can accept, drop, or reject the connections. After you
  define your accept rules, you should create a rule to drop all other traffic to prevent unauthorized access to the system.</p>
  <table border="1">
    <tbody><tr class="header">
      <td class="contentheader">Action</td>
      <td class="contentheader">Result</td>
    </tr>
    <tr>
      <td class="content">Accept</td>
      <td class="content">Allows the connection.</td>
    </tr>
    <tr>
      <td class="content">Drop</td>
      <td class="content">Drops the connection. For example, if someone pings your system, the request is dropped, and no response
      is sent to the user.</td>
    </tr>
    <tr>
      <td class="content">Reject</td>
      <td class="content">Does not allow the connection, but will send a response back. This lets the sender know that he reached a
      system, but was rejected.</td>
    </tr>
  </tbody></table>

  <h3 style="color:#F96302">Examples</h3>

  <p>These are some examples of the uses and commands for iptables. Keep in mind 
	that these are only a few examples; there are
  many more.</p>

  <table border="1">
    <tbody><tr class="header">
      <td class="contentheader">Action</td>
      <td class="contentheader">Result</td>
    </tr>
    <tr>
      <td class="content">sudo iptables -L</td>
      <td class="content">Lists all the current rules.</td>
    </tr>
    <tr>
      <td class="content">sudo iptables -F</td>
      <td class="content">Clears all the current rules.</td>
    </tr>
    <tr>
      <td class="content">sudo /sbin/iptables-save</td>
      <td class="content">Saves changes to the iptables on Ubuntu systems. The command may differ on other Linux systems.</td>
    </tr>
    <tr>
      <td class="content">sudo iptables -A INPUT -j DROP</td>
      <td class="content">Drops all incoming traffic.</td>
    </tr>
    <tr>
      <td class="content">sudo iptables -A INPUT -s 192.168.0.254 -j DROP</td>
      <td class="content">Blocks all connections associate with the IP address of 192.168.0.254.</td>
    </tr>
    <tr>
      <td class="content">sudo iptables -A OUTPUT -p tcp --dport 25 -j REJECT</td>
      <td class="content">Blocks SMTP mail on port 25.</td>
    </tr>
    <tr>
      <td class="content">sudo iptables -A INPUT -p tcp --dport 25 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT<br>
      sudo iptables -A OUTPUT -p tcp --sport 25 -m conntrack --ctstate ESTABLISHED -j ACCEPT</td>
      <td class="content">Allows SMTP mail on port 25.</td>
    </tr>
    <tr>
      <td class="content">sudo iptables -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT<br>
      sudo iptables -A OUTPUT -p tcp --sport 80 -m conntrack --ctstate ESTABLISHED -j ACCEPT</td>
      <td class="content">Allows HTTP traffic on port 80 on a web server. To allow HTTPS, you would use port 443.</td>
    </tr>
    <tr>
      <td class="content">sudo iptables -A INPUT -p tcp -m multiport --dports 80,443 -m conntrack --ctstate NEW,ESTABLISHED -j
      ACCEPT<br>
      sudo iptables -A OUTPUT -p tcp -m multiport --dports 80,443 -m conntrack --ctstate ESTABLISHED -j ACCEPT</td>
      <td class="content">Allows both HTTP and HTTPS on ports 80 and 443 on a web server.</td>
    </tr>
  </tbody></table>
</div>
</br>

## All-in-one Security Solutions 

<div id="TextViewer-root" class="TextViewer-root">
  <p>All-in-one security appliances combine many security functions into a 
	single device. These appliances are also known as unified threat management 
	(UTM) devices. These types of devices may be the best choice for:</p>

  <ul>
    <li>A small company without the budget to buy individual components.</li>
    <li>A small office without the physical space for individual components.</li>
    <li>A remote office without a technician to manage individual security 
	components.</li>
  </ul>

  <p>An all-in-one security appliance can include the following security 
	functions:</p>

  <ul>
    <li>Spam filter</li>
    <li>URL filter</li>
    <li>Web content filter</li>
    <li>Malware inspection</li>
    <li>Intrusion detection system</li>
  </ul>

  <p>All-in-one security appliances can also include the following:</p>

  <ul>
    <li>Network switch</li>
    <li>Router</li>
    <li>Firewall</li>
    <li>TX uplink (integrated CSU/DSU)</li>
    <li>Bandwidth shaping</li>
  </ul>
</div>

## Firewall Design and Implementation

<div id="TextViewer-root" class="TextViewer-root">
  <p>As you study this section, answer the following questions:</p>

  <div class="discussion">
    <ul>
      <li>How do firewalls manage incoming and outgoing traffic?</li>
      <li>What is the difference between a standard ACL and an extended ACL?</li>
      <li>What does the <b>deny any</b> statement do?</li>
      <li>What is the difference between a routed firewall and a transparent firewall?</li>
    </ul>
  </div>

  <p>In this section, you will learn to:</p>

  <div class="skills">
    <ul>
      <li>Create Firewall ACLs.</li>
      <li>Configure a DMZ.</li>
      <li>Configure a perimeter firewall.</li>
      <li>Configure a proxy server.</li>
    </ul>
  </div>

  <p>The key terms for this section include:</p>

  <table class="terms" border="1">
    <tbody><tr class="header">
      <td class="centered">Term</td>
      <td class="contentheader">Definition</td>
    </tr>
    <tr>
      <td class="centered">Demilitarized Zone<br>
      (DMZ)</td>
      <td class="content">A buffer network (or subnet) that sits between the private network and an untrusted network (such as the internet).</td>
    </tr>
    <tr>
      <td class="centered">Access Control List</td>
      <td class="content">Filtering rules firewalls use to identify which traffic 
		to allow and which to block.</td>
    </tr>
    <tr>
      <td class="centered">Routed Firewall</td>
      <td class="content">A routed firewall is a Layer 3 router. Many hardware routers include firewall functionality. Transmitting
      data through this type of firewall counts as a router hop. A routed firewall usually supports multiple interfaces, each
      connected to a different network segment.</td>
    </tr>
    <tr>
      <td class="centered">Transparent Firewall</td>
      <td class="content">A transparent firewall, also called a virtual 
		firewall, operates at Layer 2 and is not seen as a router hop by 
		connected devices. Both the internal and external interfaces on a 
		transparent firewall connect to the same network segment.</td>
    </tr>
  </tbody></table>
</div>
</br/>
<div>

  <p>A <i>demilitarized zone</i> (DMZ) is a buffer network (or subnet) that sits 
	between the private network and an untrusted network (such as the internet).</p>

  <ul>
    <li>Create a DMZ by performing the following:
      <ul>
        <li>Configure two firewall devices, one connected to the public network 
		and one connected to the private network.</li>
        <li>Configure a single device with three network cards, one connected to 
		the public network, one connected to the private network, and one 
		connected to the screened subnet.</li>
        <li>Configure a single device with two network cards, one connected to 
		the public network and another connected to a private subnet containing 
		hosts that are accessible from the private network. Configure proxy ARP 
		so the public interface of the firewall device responds to ARP requests 
		for the public IP address of the device.</li>
      </ul>
    </li>
    <li>Publicly accessible resources (servers) are placed inside the screened 
	subnet. Examples of publicly accessible resources include web, FTP, or email 
	servers.</li>
    <li>Packet filters on the outer firewall allow traffic directed to the 
	public resources inside the DMZ. Packet filters on the inner firewall 
	prevent unauthorized traffic from reaching the private network.</li>
    <li>If the firewall managing traffic into the DMZ fails, only the servers in 
	the DMZ are subject to compromise. The LAN is protected by default.</li>
    <li>When designing the outer firewall packet filters, a common practice is 
	to close all ports and open only the ports necessary for accessing the 
	public resources inside the DMZ.</li>
    <li>Typically, firewalls allow traffic that originates&nbsp; in the secured 
	internal network into the DMZ and through to the internet. Traffic that 
	originates in the DMZ (low-security area) or the internet (no-security area) 
	should not be allowed access to the intranet (high-security area).</li>
  </ul>

  <blockquote class="info">
    Do not place any server in the DMZ that doesn't have to be there.
  </blockquote>

  <h3 style="color:#F96302">Firewall Types</h3>

  <p>There are two types of firewalls:</p>

  <ul>
    <li>A <i>routed firewall</i>, is also a Layer 3 router. In fact, many 
	hardware routers include firewall functionality. Transmitting data through 
	this type of firewall counts as a router hop. A routed firewall usually 
	supports multiple interfaces, each connected to a different network segment.</li>
    <li>A <i>transparent firewall</i>, also called a <i>virtual firewall</i>, 
	operates at Layer 2 and is not seen as a router hop by connected devices. 
	Both the internal and external interfaces on a transparent firewall connect 
	to the same network segment. Because it is not a router, you can easily 
	introduce a transparent firewall into an existing network.</li>
  </ul>

<h3 style="color:#F96302">Access Control List (ACL)</h3>

  <p><i>Access control lists</i> (ACLs) are rules firewalls use to manage 
	incoming or outgoing traffic. You should be familiar with the following ACL 
	characteristics:</p>

  <ul>
    <li>ACLs describe the traffic type that will be controlled.</li>
    <li>ACL entries:
      <ul>
        <li>Describe traffic characteristics.</li>
        <li>Identify permitted and denied traffic.</li>
        <li>Can describe a specific traffic type, allow all traffic, or restrict 
		all traffic.</li>
      </ul>
    </li>
    <li>An ACL usually contains an implicit <b>deny any</b> entry at the end of 
	the list.</li>
    <li>Each ACL applies only to a specific protocol.</li>
    <li>Each router interface can have up to two ACLs for each protocol, one for 
	incoming traffic and one for outgoing traffic.</li>
    <li>When an ACL is applied to an interface, it identifies whether the list 
	restricts incoming or outgoing traffic.</li>
    <li>Each ACL can be applied to more than one interface. However, each 
	interface can have only one incoming list and one outgoing list.</li>
    <li>ACLs can be used to log traffic that matches the list statements.</li>
  </ul>

  <blockquote class="info">
    Many hardware routers, such as those from Cisco, also provide a packet 
	filtering firewall. These devices are frequently used to fill both network 
	roles (router and firewall) at the same time.
  </blockquote>

  <p>When you create an ACL on a Cisco device, a <b>deny any</b> statement is 
	automatically added at the end of the list (this statement does not appear 
	in the list itself). For a list to allow any traffic, it must have at least 
	one permit statement that either permits a specific traffic type or permits 
	all traffic not specifically restricted.</p>

  <p>There are two general types of access lists used on Cisco devices:</p>

  <table border="1">
    <tbody>
      <tr class="header">
        <td class="Centered">Access List Type</td>
        <td class="contentheader">Characteristics</td>
      </tr>
      <tr>
        <td class="Centered">Standard ACL</td>
        <td class="content">
          Standard ACLs:
          <ul>
            <li>Can filter only on source host name or host IP address.</li>
            <li>Should be placed as close to the destination as possible.</li>
            <li>Use the following number ranges:
              <ul>
                <li>1–99</li>
                <li>1300–1999</li>
              </ul>
            </li>
          </ul>
        </td>
      </tr>
      <tr>
        <td class="Centered">Extended ACL</td>
        <td class="content">
          Extended ACLs:
          <ul>
            <li>Can filter by:
              <ul>
                <li>Source IP protocol (IP, TCP, UDP, and so on)</li>
                <li>Source host name or host IP address</li>
                <li>Source or destination socket number</li>
                <li>Destination host name or host IP address</li>
                <li>Precedence or TOS values</li>
              </ul>
            </li>
            <li>Should be placed as close to the source as possible.</li>
            <li>Use the following number ranges:
              <ul>
                <li>100–199</li>
                <li>2000–2699</li>
              </ul>
            </li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
</div>

