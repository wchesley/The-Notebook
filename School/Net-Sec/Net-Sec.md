# Network Security and Data Communications

#### WTAMU CIDM-3385

# Chapter 7 Routing: 

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

| Term                              | Definition                                                                                                                                                                                             |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
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

| Type                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Dynamic NAT            | Dynamic NAT automatically maps internal IP addresses with a dynamic port assignment. On the NAT device, the internal device is identified by the public IP address and the dynamic port number. Dynamic NAT allows internal (private) hosts to contact external (public) hosts, but not vice versa—external hosts cannot initiate communications with internal hosts. This implementation is also sometimes called many-to-one NAT because many internal private IP address are mapped to one public IP address on the NAT router.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Static NAT (SNAT)      | Static NAT maps a single private IP address to a single public IP address on the NAT router. Static NAT is used to take a server on the private network (such as a web server) and make it available on the internet. Using a static mapping allows external hosts to contact internal hosts—external hosts contact the internal server using the public IP address and the static port. This implementation is called one-to-one NAT because one private IP address is mapped to one public IP address. In addition to static NAT, the term SNAT also means source NAT, stateful NAT, and secure NAT. Although the terms vary, the function is the same. One commonly used implementation of static NAT is called port forwarding. Port forwarding allows incoming traffic addressed to a specific port to move through the firewall and be transparently forwarded to a specific host on the private network. Inbound requests are addressed to the port used by the internal service on the router's public IP address (such as port 80 for a web server). This is often called the public port. Port forwarding associates the inbound port number with the IP address and port of a host on the private network. This port is often called the private port. Based on the public port number, incoming traffic is redirected to the private IP address and port of the destination host on the internal network. Port forwarding is also called destination network address translation, or DNAT. |
| Dynamic and Static NAT | Dynamic and static NAT, where two IP addresses are given to the public NAT interface (one for dynamic NAT and one for static NAT), allows traffic to flow in both directions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

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
