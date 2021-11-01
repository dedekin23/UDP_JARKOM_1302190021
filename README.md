# UDP_JARKOM_1302190021

Algoritma Dijkstra adalah sebuah algoritma yang dipakai dalam memecahkan permasalahan jarak terpendek untuk sebuah graf berarah.

Input :

``` 
int main()
{
	/* Let us create the example graph discussed above */
	int graph[V][V] = { { 0, 4, 0, 0, 0, 0, 0, 8, 0 },
			    { 4, 0, 8, 0, 0, 0, 0, 11, 0 },
			    { 0, 8, 0, 7, 0, 4, 0, 0, 2 },
			    { 0, 0, 7, 0, 9, 14, 0, 0, 0 },
			    { 0, 0, 0, 9, 0, 10, 0, 0, 0 },
			    { 0, 0, 4, 14, 10, 0, 2, 0, 0 },
			    { 0, 0, 0, 0, 0, 2, 0, 1, 6 },
			    { 8, 11, 0, 0, 0, 0, 1, 0, 7 },
			    { 0, 0, 2, 0, 0, 0, 6, 7, 0 } };

	dijkstra(graph, 0);

	return 0;
}
```

Output : 

```
Vertex Distance from Source
0 		 0
1 		 4
2 		 12
3 		 19
4 		 21
5 		 11
6 		 9
7 		 8
8 		 14
```



---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# udp-packet

# encode example

``` js
var udp = require('udp-packet')

console.log(udp.encode({
  sourceIp: '10.0.0.1',
  sourcePort: 58936,
  destinationIp: '10.0.0.2',
  destinationPort: 80,
  data: Buffer('whatever')
}))
```

output:

```
<Buffer e6 38 00 50 00 10 61 7d 77 68 61 74 65 76 65 72>
```

# decode example

``` js
var udp = require('udp-packet')
var buf = Buffer([
  0xea, 0x61, 0xe2, 0xde, 0x00, 0x50, 0xd5, 0x20, 0x80, 0x00, 0x00, 0x00, 0x00,
  0x04, 0x41, 0x81, 0xc6, 0xe0, 0x46, 0xba, 0xfd, 0xc6, 0x87, 0x22, 0x10, 0xd7,
  0xeb, 0xda, 0xd7, 0x4f, 0x62, 0x45, 0xac, 0x6b, 0xce, 0x7e, 0x6a, 0x8d, 0x4d,
  0xbc, 0xd2, 0x57, 0x32, 0x76, 0xcf, 0xa0, 0xde, 0x22, 0x38, 0xf7, 0xe0, 0xd8,
  0xee, 0x6e, 0xe0, 0xa1, 0xe8, 0xb3, 0x3e, 0x29, 0x6e, 0x08, 0x9a, 0x4a, 0xad,
  0x6e, 0x51, 0xed, 0x0b, 0xf6, 0x13, 0xff, 0xd8, 0x24, 0xbf, 0xba, 0xa4, 0x0b,
  0x05, 0xad
])
console.log(udp.decode(buf))
```

output:

```
{ sourcePort: 60001,
  destinationPort: 58078,
  length: 80,
  checksum: 54560,
  data: <Buffer 80 00 00 00 00 04 41 81 c6 e0 46 ba fd c6 87 22 10 d7 eb da d7 4f 62 45 ac 6b ce 7e 6a 8d 4d bc d2 57 32 76 cf a0 de 22 38 f7 e0 d8 ee 6e e0 a1 e8 b3 ... > }
```

# api

``` js
var udp = require('udp-packet')
```

## var buf = udp.encode(packet)

Encode a `packet`:

* `packet.sourcePort`
* `packet.destinationPort`
* `packet.data` - buffer payload

Optionally, for checksums:

* `packet.sourceIp` - ipv4 address string or 4-byte buffer
* `packet.destinationIp` - ipv4 address string or 4-byte buffer
* `packet.protocol` - [protocol number](https://en.wikipedia.org/wiki/List_of_IP_protocol_numbers) (default: 0x11 for UDP)

## var packet = udp.decode(buf)

Decode a given a UDP data packet `buf`:

* `packet.sourcePort`
* `packet.destinationPort`
* `packet.length` - length of total udp packet, including 8 byte header
* `packet.checksum`
* `packet.data`

## var sum = udp.checksum(packet, buffer)

Return the checksum for a decoded `packet`.

# install

```
npm install udp-packet
```

# license

MIT
