# self_auth_info

This struct contains authorization information. The PS4 rely on this struct to determine what actions can be done for each thread. The PS4 obtained this struct from application image through the SAMU. Some examples of this structs can be found [here](https://www.psdevwiki.com/ps4/Auth_Info).

| 9.0  | Type   | Name  | Description |
| ---- | ------ | ----- | ----------- |
| 0x00 | u64    | paid  | [Program Authority ID](https://www.psdevwiki.com/ps4/Program_Authority_ID) |
| 0x08 | u64[4] | caps  | Bit flags indicated what permissions are allowed. |
| 0x28 | u64[4] | attrs ||
| 0x48 | u8[64] |       ||
