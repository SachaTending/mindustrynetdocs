Header in packets used for identification of packets

Also, header contains flag(if packet payload compressed)

Packet payload is after header

Header for non-framework packets


| Name           | Type        | Description                                                                        |
| :--------------- | ------------- | ------------------------------------------------------------------------------------ |
| Packet ID      | uint8       | Packet ID(If value is 0xfe(-2), packet is a framework packet)                      |
| Size           | uint16      | Packet size(uncompressed size for compressed packets)                              |
| Is compressed? | uint8(bool) | Is packet compressed, if value 1, client/server should uncompress packet using LZ4 |

Header for framework packets


| Name                 | Type  | Description                                                                                |
| ---------------------- | ------- | -------------------------------------------------------------------------------------------- |
| Is framework packet? | uint8 | If value is 0xfe(-2, signed), client/server should intrepritate packet as framework packet |

Packet is only compressed when it's serialized size over 36 bytes(Anuken, why?), except for stream packets

Packet header is not generated when ArcNetProvider when generating packet header gets ByteBuffer as packet
