# getcontractopcode方法

获取合约脚本的指令解析

## 参数说明

hex：合约脚本

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getcontractopcode",
  "params": ["53c56b6c766b00527ac46c766b51527ac46168044e02db0663240061148226c513e2aa717f2f32d3c5fb2bcb492acfc3dc6168042aa0d63c616c75666168044e02db0660907c907c9e63100161680445995a5c6a52527ac46a00c30962616c616e63654f66876412006a51c300c361e00101ed00616c75666a00c308646563696d616c7387640d0061e001003f01616c75666a00c3066465706c6f7987640d0061e001002f01616c75666a00c3046e616d6587640d0061e00100e301616c75666a00c30673796d626f6c87640d0061e00100da01616c75666a00c312737570706f727465645374616e646172647387640d0061e00100c101616c75666a00c30b746f74616c537570706c7987640d0061e00100d301616c75666a00c3087472616e73666572876433006a51c300c36a51c351c36a51c352c36a52c3615379517955727551727552795279547275527275e00104f601616c756600616c756651c56b6c766b00527ac46a00c3c001149c6339003254686520706172616d65746572206163636f756e742053484f554c442062652032302d62797465206164647265737365732e6175f0616804f6e65d34056173736574617ce001023a036a00c3617ce001025603616c756600c56b58616c756600c56b61e001000d01009e64080000616c7566616804f6e65d3408636f6e7472616374617ce00102fa020b746f74616c537570706c7961070000c16ff28623615272e000033903616804f6e65d34056173736574617ce00102c90261148226c513e2aa717f2f32d3c5fb2bcb492acfc3dc61070000c16ff28623615272e000033f03610061148226c513e2aa717f2f32d3c5fb2bcb492acfc3dc61070000c16ff28623615272087472616e7366657254c168124268702e52756e74696d652e4e6f7469667951616c756600c56b074d794252433230616c756600c56b034d5942616c756600c56b54c57600054252432d35c47651054252432d37c47652064252432d3130c47653064252432d3230c4616c756600c56b616804f6e65d3408636f6e7472616374617ce00102f7010b746f74616c537570706c79617ce00102c202616c756652c56b6c766b00527ac46a00c361680472360ef76a51527ac46a51c36411006a51c36168041c5de8d2616c756651616c756657c56b6c766b00527ac46c766b51527ac46c766b52527ac46c766b53527ac46a00c3c00114907c907c9e630d006a51c3c001149c633e003754686520706172616d65746572732066726f6d20616e6420746f2053484f554c442062652032302d62797465206164647265737365732e6175f06a52c300a16433002c54686520706172616d6574657220616d6f756e74204d5553542062652067726561746572207468616e20302e6175f06a51c361e001011eff63080000616c75666a00c36168042aa0d63c6312006a00c36a53c39e64080000616c7566616804f6e65d34056173736574617ce00102c3006a54527ac46a54c36a00c3617ce00102d7006a55527ac46a55c36a52c39f64080000616c75666a00c36a51c3907c907c9e63080051616c75666a55c36a52c39c6413006a54c36a00c3617ce0000287016218006a54c36a00c36a55c36a52c394615272e00003f8006a54c36a51c3617ce0010274006a56527ac46a54c36a51c36a56c36a52c393615272e00003d100616a00c36a51c36a52c3615272087472616e7366657254c168124268702e52756e74696d652e4e6f7469667951616c756652c56b6c766b00527ac46c766b51527ac46152c5766a00c3007cc4766a51c3517cc4616c756653c56b6c766b00527ac46c766b51527ac46a00c351c301007e6a51c37e6a52527ac46a00c300c36a52c3617c6804af270b05616c756654c56b6c766b00527ac46c766b51527ac46c766b52527ac46a00c351c301007e6a51c37e6a53527ac46a00c300c36a53c36a52c36152726804a65593fc616c756654c56b6c766b00527ac46c766b51527ac46c766b52527ac46a00c351c301007e6a51c37e6a53527ac46a00c300c36a53c36a52c36152726804a65593fc616c756653c56b6c766b00527ac46c766b51527ac46a00c351c301007e6a51c37e6a52527ac46a00c300c36a52c3617c6804af270b05616c756653c56b6c766b00527ac46c766b51527ac46a00c351c301007e6a51c37e6a52527ac46a00c300c36a52c3617c68045dabecb3616c7566"],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "opcode": [
            "0000:PUSH3",
            "0001:NEWARRAY",
            "0002:TOALTSTACK",
            "0003:FROMALTSTACK",
            "0004:DUP",
            "0005:TOALTSTACK",
            "0006:PUSH0(false)",
            "0007:PUSH2",
            "0008:ROLL",
            "0009:SETITEM",
            "000a:FROMALTSTACK",
            "000b:DUP",
            "000c:TOALTSTACK",
            "000d:PUSH1(true)",
            "000e:PUSH2",
            "000f:ROLL",
            "0010:SETITEM",
            "0011:NOP",
            "0012:SYSCALL[0x4e02db06]",
            "0018:JMPIF[36]",
            "001b:NOP",
            "001c:PUSHBYTES20[0x8226c513e2aa717f2f32d3c5fb2bcb492acfc3dc]",
            "0031:NOP",
            "0032:SYSCALL[0x2aa0d63c]",
            "0038:NOP",
            "0039:FROMALTSTACK",
            "003a:DROP",
            "003b:RET",
            "003c:NOP",
            "003d:SYSCALL[0x4e02db06]",
            "0043:PUSH16",
            "0044:ABS",
            "0045:SWAP",
            "0046:ABS",
            "0047:SWAP",
            "0048:NUMNOTEQUAL",
            "0049:JMPIF[272]",
            "004c:NOP",
            "004d:SYSCALL[0x45995a5c]",
            "0053:DUPFROMALTSTACK",
            "0054:PUSH2",
            "0055:PUSH2",
            "0056:ROLL",
            "0057:SETITEM",
            "0058:DUPFROMALTSTACK",
            "0059:PUSH0(false)",
            "005a:PICKITEM",
            "005b:PUSHBYTES9[0x62616c616e63654f66]",
            "0065:EQUAL",
            "0066:JMPIFNOT[18]",
            "0069:DUPFROMALTSTACK",
            "006a:PUSH1(true)",
            "006b:PICKITEM",
            "006c:PUSH0(false)",
            "006d:PICKITEM",
            "006e:NOP",
            "006f:CALL_I",
            "0074:NOP",
            "0075:FROMALTSTACK",
            "0076:DROP",
            "0077:RET",
            "0078:DUPFROMALTSTACK",
            "0079:PUSH0(false)",
            "007a:PICKITEM",
            "007b:PUSHBYTES8[0x646563696d616c73]",
            "0084:EQUAL",
            "0085:JMPIFNOT[13]",
            "0088:NOP",
            "0089:CALL_I",
            "008e:NOP",
            "008f:FROMALTSTACK",
            "0090:DROP",
            "0091:RET",
            "0092:DUPFROMALTSTACK",
            "0093:PUSH0(false)",
            "0094:PICKITEM",
            "0095:PUSHBYTES6[0x6465706c6f79]",
            "009c:EQUAL",
            "009d:JMPIFNOT[13]",
            "00a0:NOP",
            "00a1:CALL_I",
            "00a6:NOP",
            "00a7:FROMALTSTACK",
            "00a8:DROP",
            "00a9:RET",
            "00aa:DUPFROMALTSTACK",
            "00ab:PUSH0(false)",
            "00ac:PICKITEM",
            "00ad:PUSHBYTES4[0x6e616d65]",
            "00b2:EQUAL",
            "00b3:JMPIFNOT[13]",
            "00b6:NOP",
            "00b7:CALL_I",
            "00bc:NOP",
            "00bd:FROMALTSTACK",
            "00be:DROP",
            "00bf:RET",
            "00c0:DUPFROMALTSTACK",
            "00c1:PUSH0(false)",
            "00c2:PICKITEM",
            "00c3:PUSHBYTES6[0x73796d626f6c]",
            "00ca:EQUAL",
            "00cb:JMPIFNOT[13]",
            "00ce:NOP",
            "00cf:CALL_I",
            "00d4:NOP",
            "00d5:FROMALTSTACK",
            "00d6:DROP",
            "00d7:RET",
            "00d8:DUPFROMALTSTACK",
            "00d9:PUSH0(false)",
            "00da:PICKITEM",
            "00db:PUSHBYTES18[0x737570706f727465645374616e6461726473]",
            "00ee:EQUAL",
            "00ef:JMPIFNOT[13]",
            "00f2:NOP",
            "00f3:CALL_I",
            "00f8:NOP",
            "00f9:FROMALTSTACK",
            "00fa:DROP",
            "00fb:RET",
            "00fc:DUPFROMALTSTACK",
            "00fd:PUSH0(false)",
            "00fe:PICKITEM",
            "00ff:PUSHBYTES11[0x746f74616c537570706c79]",
            "010b:EQUAL",
            "010c:JMPIFNOT[13]",
            "010f:NOP",
            "0110:CALL_I",
            "0115:NOP",
            "0116:FROMALTSTACK",
            "0117:DROP",
            "0118:RET",
            "0119:DUPFROMALTSTACK",
            "011a:PUSH0(false)",
            "011b:PICKITEM",
            "011c:PUSHBYTES8[0x7472616e73666572]",
            "0125:EQUAL",
            "0126:JMPIFNOT[51]",
            "0129:DUPFROMALTSTACK",
            "012a:PUSH1(true)",
            "012b:PICKITEM",
            "012c:PUSH0(false)",
            "012d:PICKITEM",
            "012e:DUPFROMALTSTACK",
            "012f:PUSH1(true)",
            "0130:PICKITEM",
            "0131:PUSH1(true)",
            "0132:PICKITEM",
            "0133:DUPFROMALTSTACK",
            "0134:PUSH1(true)",
            "0135:PICKITEM",
            "0136:PUSH2",
            "0137:PICKITEM",
            "0138:DUPFROMALTSTACK",
            "0139:PUSH2",
            "013a:PICKITEM",
            "013b:NOP",
            "013c:PUSH3",
            "013d:PICK",
            "013e:PUSH1(true)",
            "013f:PICK",
            "0140:PUSH5",
            "0141:XSWAP",
            "0142:DROP",
            "0143:PUSH1(true)",
            "0144:XSWAP",
            "0145:DROP",
            "0146:PUSH2",
            "0147:PICK",
            "0148:PUSH2",
            "0149:PICK",
            "014a:PUSH4",
            "014b:XSWAP",
            "014c:DROP",
            "014d:PUSH2",
            "014e:XSWAP",
            "014f:DROP",
            "0150:CALL_I",
            "0155:NOP",
            "0156:FROMALTSTACK",
            "0157:DROP",
            "0158:RET",
            "0159:PUSH0(false)",
            "015a:NOP",
            "015b:FROMALTSTACK",
            "015c:DROP",
            "015d:RET",
            "015e:PUSH1(true)",
            "015f:NEWARRAY",
            "0160:TOALTSTACK",
            "0161:FROMALTSTACK",
            "0162:DUP",
            "0163:TOALTSTACK",
            "0164:PUSH0(false)",
            "0165:PUSH2",
            "0166:ROLL",
            "0167:SETITEM",
            "0168:DUPFROMALTSTACK",
            "0169:PUSH0(false)",
            "016a:PICKITEM",
            "016b:ARRAYSIZE",
            "016c:PUSHBYTES1[0x14]",
            "016e:NUMEQUAL",
            "016f:JMPIF[57]",
            "0172:PUSHBYTES50[0x54686520706172616d65746572206163636f756e742053484f554c442062652032302d62797465206164647265737365732e]",
            "01a5:NOP",
            "01a6:DROP",
            "01a7:THROW",
            "01a8:NOP",
            "01a9:SYSCALL[0xf6e65d34]",
            "01af:PUSHBYTES5[0x6173736574]",
            "01b5:NOP",
            "01b6:SWAP",
            "01b7:CALL_I",
            "01bc:DUPFROMALTSTACK",
            "01bd:PUSH0(false)",
            "01be:PICKITEM",
            "01bf:NOP",
            "01c0:SWAP",
            "01c1:CALL_I",
            "01c6:NOP",
            "01c7:FROMALTSTACK",
            "01c8:DROP",
            "01c9:RET",
            "01ca:PUSH0(false)",
            "01cb:NEWARRAY",
            "01cc:TOALTSTACK",
            "01cd:PUSH8",
            "01ce:NOP",
            "01cf:FROMALTSTACK",
            "01d0:DROP",
            "01d1:RET",
            "01d2:PUSH0(false)",
            "01d3:NEWARRAY",
            "01d4:TOALTSTACK",
            "01d5:NOP",
            "01d6:CALL_I",
            "01db:PUSH0(false)",
            "01dc:NUMNOTEQUAL",
            "01dd:JMPIFNOT[8]",
            "01e0:PUSH0(false)",
            "01e1:NOP",
            "01e2:FROMALTSTACK",
            "01e3:DROP",
            "01e4:RET",
            "01e5:NOP",
            "01e6:SYSCALL[0xf6e65d34]",
            "01ec:PUSHBYTES8[0x636f6e7472616374]",
            "01f5:NOP",
            "01f6:SWAP",
            "01f7:CALL_I",
            "01fc:PUSHBYTES11[0x746f74616c537570706c79]",
            "0208:NOP",
            "0209:PUSHBYTES7[0x0000c16ff28623]",
            "0211:NOP",
            "0212:PUSH2",
            "0213:XSWAP",
            "0214:CALL_I",
            "0219:NOP",
            "021a:SYSCALL[0xf6e65d34]",
            "0220:PUSHBYTES5[0x6173736574]",
            "0226:NOP",
            "0227:SWAP",
            "0228:CALL_I",
            "022d:NOP",
            "022e:PUSHBYTES20[0x8226c513e2aa717f2f32d3c5fb2bcb492acfc3dc]",
            "0243:NOP",
            "0244:PUSHBYTES7[0x0000c16ff28623]",
            "024c:NOP",
            "024d:PUSH2",
            "024e:XSWAP",
            "024f:CALL_I",
            "0254:NOP",
            "0255:PUSH0(false)",
            "0256:NOP",
            "0257:PUSHBYTES20[0x8226c513e2aa717f2f32d3c5fb2bcb492acfc3dc]",
            "026c:NOP",
            "026d:PUSHBYTES7[0x0000c16ff28623]",
            "0275:NOP",
            "0276:PUSH2",
            "0277:XSWAP",
            "0278:PUSHBYTES8[0x7472616e73666572]",
            "0281:PUSH4",
            "0282:PACK",
            "0283:SYSCALL[Bhp.Runtime.Notify]",
            "0297:PUSH1(true)",
            "0298:NOP",
            "0299:FROMALTSTACK",
            "029a:DROP",
            "029b:RET",
            "029c:PUSH0(false)",
            "029d:NEWARRAY",
            "029e:TOALTSTACK",
            "029f:PUSHBYTES7[0x4d794252433230]",
            "02a7:NOP",
            "02a8:FROMALTSTACK",
            "02a9:DROP",
            "02aa:RET",
            "02ab:PUSH0(false)",
            "02ac:NEWARRAY",
            "02ad:TOALTSTACK",
            "02ae:PUSHBYTES3[0x4d5942]",
            "02b2:NOP",
            "02b3:FROMALTSTACK",
            "02b4:DROP",
            "02b5:RET",
            "02b6:PUSH0(false)",
            "02b7:NEWARRAY",
            "02b8:TOALTSTACK",
            "02b9:PUSH4",
            "02ba:NEWARRAY",
            "02bb:DUP",
            "02bc:PUSH0(false)",
            "02bd:PUSHBYTES5[0x4252432d35]",
            "02c3:SETITEM",
            "02c4:DUP",
            "02c5:PUSH1(true)",
            "02c6:PUSHBYTES5[0x4252432d37]",
            "02cc:SETITEM",
            "02cd:DUP",
            "02ce:PUSH2",
            "02cf:PUSHBYTES6[0x4252432d3130]",
            "02d6:SETITEM",
            "02d7:DUP",
            "02d8:PUSH3",
            "02d9:PUSHBYTES6[0x4252432d3230]",
            "02e0:SETITEM",
            "02e1:NOP",
            "02e2:FROMALTSTACK",
            "02e3:DROP",
            "02e4:RET",
            "02e5:PUSH0(false)",
            "02e6:NEWARRAY",
            "02e7:TOALTSTACK",
            "02e8:NOP",
            "02e9:SYSCALL[0xf6e65d34]",
            "02ef:PUSHBYTES8[0x636f6e7472616374]",
            "02f8:NOP",
            "02f9:SWAP",
            "02fa:CALL_I",
            "02ff:PUSHBYTES11[0x746f74616c537570706c79]",
            "030b:NOP",
            "030c:SWAP",
            "030d:CALL_I",
            "0312:NOP",
            "0313:FROMALTSTACK",
            "0314:DROP",
            "0315:RET",
            "0316:PUSH2",
            "0317:NEWARRAY",
            "0318:TOALTSTACK",
            "0319:FROMALTSTACK",
            "031a:DUP",
            "031b:TOALTSTACK",
            "031c:PUSH0(false)",
            "031d:PUSH2",
            "031e:ROLL",
            "031f:SETITEM",
            "0320:DUPFROMALTSTACK",
            "0321:PUSH0(false)",
            "0322:PICKITEM",
            "0323:NOP",
            "0324:SYSCALL[0x72360ef7]",
            "032a:DUPFROMALTSTACK",
            "032b:PUSH1(true)",
            "032c:PUSH2",
            "032d:ROLL",
            "032e:SETITEM",
            "032f:DUPFROMALTSTACK",
            "0330:PUSH1(true)",
            "0331:PICKITEM",
            "0332:JMPIFNOT[17]",
            "0335:DUPFROMALTSTACK",
            "0336:PUSH1(true)",
            "0337:PICKITEM",
            "0338:NOP",
            "0339:SYSCALL[0x1c5de8d2]",
            "033f:NOP",
            "0340:FROMALTSTACK",
            "0341:DROP",
            "0342:RET",
            "0343:PUSH1(true)",
            "0344:NOP",
            "0345:FROMALTSTACK",
            "0346:DROP",
            "0347:RET",
            "0348:PUSH7",
            "0349:NEWARRAY",
            "034a:TOALTSTACK",
            "034b:FROMALTSTACK",
            "034c:DUP",
            "034d:TOALTSTACK",
            "034e:PUSH0(false)",
            "034f:PUSH2",
            "0350:ROLL",
            "0351:SETITEM",
            "0352:FROMALTSTACK",
            "0353:DUP",
            "0354:TOALTSTACK",
            "0355:PUSH1(true)",
            "0356:PUSH2",
            "0357:ROLL",
            "0358:SETITEM",
            "0359:FROMALTSTACK",
            "035a:DUP",
            "035b:TOALTSTACK",
            "035c:PUSH2",
            "035d:PUSH2",
            "035e:ROLL",
            "035f:SETITEM",
            "0360:FROMALTSTACK",
            "0361:DUP",
            "0362:TOALTSTACK",
            "0363:PUSH3",
            "0364:PUSH2",
            "0365:ROLL",
            "0366:SETITEM",
            "0367:DUPFROMALTSTACK",
            "0368:PUSH0(false)",
            "0369:PICKITEM",
            "036a:ARRAYSIZE",
            "036b:PUSHBYTES1[0x14]",
            "036d:ABS",
            "036e:SWAP",
            "036f:ABS",
            "0370:SWAP",
            "0371:NUMNOTEQUAL",
            "0372:JMPIF[13]",
            "0375:DUPFROMALTSTACK",
            "0376:PUSH1(true)",
            "0377:PICKITEM",
            "0378:ARRAYSIZE",
            "0379:PUSHBYTES1[0x14]",
            "037b:NUMEQUAL",
            "037c:JMPIF[62]",
            "037f:PUSHBYTES55[0x54686520706172616d65746572732066726f6d20616e6420746f2053484f554c442062652032302d62797465206164647265737365732e]",
            "03b7:NOP",
            "03b8:DROP",
            "03b9:THROW",
            "03ba:DUPFROMALTSTACK",
            "03bb:PUSH2",
            "03bc:PICKITEM",
            "03bd:PUSH0(false)",
            "03be:LTE",
            "03bf:JMPIFNOT[51]",
            "03c2:PUSHBYTES44[0x54686520706172616d6574657220616d6f756e74204d5553542062652067726561746572207468616e20302e]",
            "03ef:NOP",
            "03f0:DROP",
            "03f1:THROW",
            "03f2:DUPFROMALTSTACK",
            "03f3:PUSH1(true)",
            "03f4:PICKITEM",
            "03f5:NOP",
            "03f6:CALL_I",
            "03fb:JMPIF[8]",
            "03fe:PUSH0(false)",
            "03ff:NOP",
            "0400:FROMALTSTACK",
            "0401:DROP",
            "0402:RET",
            "0403:DUPFROMALTSTACK",
            "0404:PUSH0(false)",
            "0405:PICKITEM",
            "0406:NOP",
            "0407:SYSCALL[0x2aa0d63c]",
            "040d:JMPIF[18]",
            "0410:DUPFROMALTSTACK",
            "0411:PUSH0(false)",
            "0412:PICKITEM",
            "0413:DUPFROMALTSTACK",
            "0414:PUSH3",
            "0415:PICKITEM",
            "0416:NUMNOTEQUAL",
            "0417:JMPIFNOT[8]",
            "041a:PUSH0(false)",
            "041b:NOP",
            "041c:FROMALTSTACK",
            "041d:DROP",
            "041e:RET",
            "041f:NOP",
            "0420:SYSCALL[0xf6e65d34]",
            "0426:PUSHBYTES5[0x6173736574]",
            "042c:NOP",
            "042d:SWAP",
            "042e:CALL_I",
            "0433:DUPFROMALTSTACK",
            "0434:PUSH4",
            "0435:PUSH2",
            "0436:ROLL",
            "0437:SETITEM",
            "0438:DUPFROMALTSTACK",
            "0439:PUSH4",
            "043a:PICKITEM",
            "043b:DUPFROMALTSTACK",
            "043c:PUSH0(false)",
            "043d:PICKITEM",
            "043e:NOP",
            "043f:SWAP",
            "0440:CALL_I",
            "0445:DUPFROMALTSTACK",
            "0446:PUSH5",
            "0447:PUSH2",
            "0448:ROLL",
            "0449:SETITEM",
            "044a:DUPFROMALTSTACK",
            "044b:PUSH5",
            "044c:PICKITEM",
            "044d:DUPFROMALTSTACK",
            "044e:PUSH2",
            "044f:PICKITEM",
            "0450:LT",
            "0451:JMPIFNOT[8]",
            "0454:PUSH0(false)",
            "0455:NOP",
            "0456:FROMALTSTACK",
            "0457:DROP",
            "0458:RET",
            "0459:DUPFROMALTSTACK",
            "045a:PUSH0(false)",
            "045b:PICKITEM",
            "045c:DUPFROMALTSTACK",
            "045d:PUSH1(true)",
            "045e:PICKITEM",
            "045f:ABS",
            "0460:SWAP",
            "0461:ABS",
            "0462:SWAP",
            "0463:NUMNOTEQUAL",
            "0464:JMPIF[8]",
            "0467:PUSH1(true)",
            "0468:NOP",
            "0469:FROMALTSTACK",
            "046a:DROP",
            "046b:RET",
            "046c:DUPFROMALTSTACK",
            "046d:PUSH5",
            "046e:PICKITEM",
            "046f:DUPFROMALTSTACK",
            "0470:PUSH2",
            "0471:PICKITEM",
            "0472:NUMEQUAL",
            "0473:JMPIFNOT[19]",
            "0476:DUPFROMALTSTACK",
            "0477:PUSH4",
            "0478:PICKITEM",
            "0479:DUPFROMALTSTACK",
            "047a:PUSH0(false)",
            "047b:PICKITEM",
            "047c:NOP",
            "047d:SWAP",
            "047e:CALL_I",
            "0483:JMP[24]",
            "0486:DUPFROMALTSTACK",
            "0487:PUSH4",
            "0488:PICKITEM",
            "0489:DUPFROMALTSTACK",
            "048a:PUSH0(false)",
            "048b:PICKITEM",
            "048c:DUPFROMALTSTACK",
            "048d:PUSH5",
            "048e:PICKITEM",
            "048f:DUPFROMALTSTACK",
            "0490:PUSH2",
            "0491:PICKITEM",
            "0492:SUB",
            "0493:NOP",
            "0494:PUSH2",
            "0495:XSWAP",
            "0496:CALL_I",
            "049b:DUPFROMALTSTACK",
            "049c:PUSH4",
            "049d:PICKITEM",
            "049e:DUPFROMALTSTACK",
            "049f:PUSH1(true)",
            "04a0:PICKITEM",
            "04a1:NOP",
            "04a2:SWAP",
            "04a3:CALL_I",
            "04a8:DUPFROMALTSTACK",
            "04a9:PUSH6",
            "04aa:PUSH2",
            "04ab:ROLL",
            "04ac:SETITEM",
            "04ad:DUPFROMALTSTACK",
            "04ae:PUSH4",
            "04af:PICKITEM",
            "04b0:DUPFROMALTSTACK",
            "04b1:PUSH1(true)",
            "04b2:PICKITEM",
            "04b3:DUPFROMALTSTACK",
            "04b4:PUSH6",
            "04b5:PICKITEM",
            "04b6:DUPFROMALTSTACK",
            "04b7:PUSH2",
            "04b8:PICKITEM",
            "04b9:ADD",
            "04ba:NOP",
            "04bb:PUSH2",
            "04bc:XSWAP",
            "04bd:CALL_I",
            "04c2:NOP",
            "04c3:DUPFROMALTSTACK",
            "04c4:PUSH0(false)",
            "04c5:PICKITEM",
            "04c6:DUPFROMALTSTACK",
            "04c7:PUSH1(true)",
            "04c8:PICKITEM",
            "04c9:DUPFROMALTSTACK",
            "04ca:PUSH2",
            "04cb:PICKITEM",
            "04cc:NOP",
            "04cd:PUSH2",
            "04ce:XSWAP",
            "04cf:PUSHBYTES8[0x7472616e73666572]",
            "04d8:PUSH4",
            "04d9:PACK",
            "04da:SYSCALL[Bhp.Runtime.Notify]",
            "04ee:PUSH1(true)",
            "04ef:NOP",
            "04f0:FROMALTSTACK",
            "04f1:DROP",
            "04f2:RET",
            "04f3:PUSH2",
            "04f4:NEWARRAY",
            "04f5:TOALTSTACK",
            "04f6:FROMALTSTACK",
            "04f7:DUP",
            "04f8:TOALTSTACK",
            "04f9:PUSH0(false)",
            "04fa:PUSH2",
            "04fb:ROLL",
            "04fc:SETITEM",
            "04fd:FROMALTSTACK",
            "04fe:DUP",
            "04ff:TOALTSTACK",
            "0500:PUSH1(true)",
            "0501:PUSH2",
            "0502:ROLL",
            "0503:SETITEM",
            "0504:NOP",
            "0505:PUSH2",
            "0506:NEWARRAY",
            "0507:DUP",
            "0508:DUPFROMALTSTACK",
            "0509:PUSH0(false)",
            "050a:PICKITEM",
            "050b:PUSH0(false)",
            "050c:SWAP",
            "050d:SETITEM",
            "050e:DUP",
            "050f:DUPFROMALTSTACK",
            "0510:PUSH1(true)",
            "0511:PICKITEM",
            "0512:PUSH1(true)",
            "0513:SWAP",
            "0514:SETITEM",
            "0515:NOP",
            "0516:FROMALTSTACK",
            "0517:DROP",
            "0518:RET",
            "0519:PUSH3",
            "051a:NEWARRAY",
            "051b:TOALTSTACK",
            "051c:FROMALTSTACK",
            "051d:DUP",
            "051e:TOALTSTACK",
            "051f:PUSH0(false)",
            "0520:PUSH2",
            "0521:ROLL",
            "0522:SETITEM",
            "0523:FROMALTSTACK",
            "0524:DUP",
            "0525:TOALTSTACK",
            "0526:PUSH1(true)",
            "0527:PUSH2",
            "0528:ROLL",
            "0529:SETITEM",
            "052a:DUPFROMALTSTACK",
            "052b:PUSH0(false)",
            "052c:PICKITEM",
            "052d:PUSH1(true)",
            "052e:PICKITEM",
            "052f:PUSHBYTES1[0x00]",
            "0531:CAT",
            "0532:DUPFROMALTSTACK",
            "0533:PUSH1(true)",
            "0534:PICKITEM",
            "0535:CAT",
            "0536:DUPFROMALTSTACK",
            "0537:PUSH2",
            "0538:PUSH2",
            "0539:ROLL",
            "053a:SETITEM",
            "053b:DUPFROMALTSTACK",
            "053c:PUSH0(false)",
            "053d:PICKITEM",
            "053e:PUSH0(false)",
            "053f:PICKITEM",
            "0540:DUPFROMALTSTACK",
            "0541:PUSH2",
            "0542:PICKITEM",
            "0543:NOP",
            "0544:SWAP",
            "0545:SYSCALL[0xaf270b05]",
            "054b:NOP",
            "054c:FROMALTSTACK",
            "054d:DROP",
            "054e:RET",
            "054f:PUSH4",
            "0550:NEWARRAY",
            "0551:TOALTSTACK",
            "0552:FROMALTSTACK",
            "0553:DUP",
            "0554:TOALTSTACK",
            "0555:PUSH0(false)",
            "0556:PUSH2",
            "0557:ROLL",
            "0558:SETITEM",
            "0559:FROMALTSTACK",
            "055a:DUP",
            "055b:TOALTSTACK",
            "055c:PUSH1(true)",
            "055d:PUSH2",
            "055e:ROLL",
            "055f:SETITEM",
            "0560:FROMALTSTACK",
            "0561:DUP",
            "0562:TOALTSTACK",
            "0563:PUSH2",
            "0564:PUSH2",
            "0565:ROLL",
            "0566:SETITEM",
            "0567:DUPFROMALTSTACK",
            "0568:PUSH0(false)",
            "0569:PICKITEM",
            "056a:PUSH1(true)",
            "056b:PICKITEM",
            "056c:PUSHBYTES1[0x00]",
            "056e:CAT",
            "056f:DUPFROMALTSTACK",
            "0570:PUSH1(true)",
            "0571:PICKITEM",
            "0572:CAT",
            "0573:DUPFROMALTSTACK",
            "0574:PUSH3",
            "0575:PUSH2",
            "0576:ROLL",
            "0577:SETITEM",
            "0578:DUPFROMALTSTACK",
            "0579:PUSH0(false)",
            "057a:PICKITEM",
            "057b:PUSH0(false)",
            "057c:PICKITEM",
            "057d:DUPFROMALTSTACK",
            "057e:PUSH3",
            "057f:PICKITEM",
            "0580:DUPFROMALTSTACK",
            "0581:PUSH2",
            "0582:PICKITEM",
            "0583:NOP",
            "0584:PUSH2",
            "0585:XSWAP",
            "0586:SYSCALL[0xa65593fc]",
            "058c:NOP",
            "058d:FROMALTSTACK",
            "058e:DROP",
            "058f:RET",
            "0590:PUSH4",
            "0591:NEWARRAY",
            "0592:TOALTSTACK",
            "0593:FROMALTSTACK",
            "0594:DUP",
            "0595:TOALTSTACK",
            "0596:PUSH0(false)",
            "0597:PUSH2",
            "0598:ROLL",
            "0599:SETITEM",
            "059a:FROMALTSTACK",
            "059b:DUP",
            "059c:TOALTSTACK",
            "059d:PUSH1(true)",
            "059e:PUSH2",
            "059f:ROLL",
            "05a0:SETITEM",
            "05a1:FROMALTSTACK",
            "05a2:DUP",
            "05a3:TOALTSTACK",
            "05a4:PUSH2",
            "05a5:PUSH2",
            "05a6:ROLL",
            "05a7:SETITEM",
            "05a8:DUPFROMALTSTACK",
            "05a9:PUSH0(false)",
            "05aa:PICKITEM",
            "05ab:PUSH1(true)",
            "05ac:PICKITEM",
            "05ad:PUSHBYTES1[0x00]",
            "05af:CAT",
            "05b0:DUPFROMALTSTACK",
            "05b1:PUSH1(true)",
            "05b2:PICKITEM",
            "05b3:CAT",
            "05b4:DUPFROMALTSTACK",
            "05b5:PUSH3",
            "05b6:PUSH2",
            "05b7:ROLL",
            "05b8:SETITEM",
            "05b9:DUPFROMALTSTACK",
            "05ba:PUSH0(false)",
            "05bb:PICKITEM",
            "05bc:PUSH0(false)",
            "05bd:PICKITEM",
            "05be:DUPFROMALTSTACK",
            "05bf:PUSH3",
            "05c0:PICKITEM",
            "05c1:DUPFROMALTSTACK",
            "05c2:PUSH2",
            "05c3:PICKITEM",
            "05c4:NOP",
            "05c5:PUSH2",
            "05c6:XSWAP",
            "05c7:SYSCALL[0xa65593fc]",
            "05cd:NOP",
            "05ce:FROMALTSTACK",
            "05cf:DROP",
            "05d0:RET",
            "05d1:PUSH3",
            "05d2:NEWARRAY",
            "05d3:TOALTSTACK",
            "05d4:FROMALTSTACK",
            "05d5:DUP",
            "05d6:TOALTSTACK",
            "05d7:PUSH0(false)",
            "05d8:PUSH2",
            "05d9:ROLL",
            "05da:SETITEM",
            "05db:FROMALTSTACK",
            "05dc:DUP",
            "05dd:TOALTSTACK",
            "05de:PUSH1(true)",
            "05df:PUSH2",
            "05e0:ROLL",
            "05e1:SETITEM",
            "05e2:DUPFROMALTSTACK",
            "05e3:PUSH0(false)",
            "05e4:PICKITEM",
            "05e5:PUSH1(true)",
            "05e6:PICKITEM",
            "05e7:PUSHBYTES1[0x00]",
            "05e9:CAT",
            "05ea:DUPFROMALTSTACK",
            "05eb:PUSH1(true)",
            "05ec:PICKITEM",
            "05ed:CAT",
            "05ee:DUPFROMALTSTACK",
            "05ef:PUSH2",
            "05f0:PUSH2",
            "05f1:ROLL",
            "05f2:SETITEM",
            "05f3:DUPFROMALTSTACK",
            "05f4:PUSH0(false)",
            "05f5:PICKITEM",
            "05f6:PUSH0(false)",
            "05f7:PICKITEM",
            "05f8:DUPFROMALTSTACK",
            "05f9:PUSH2",
            "05fa:PICKITEM",
            "05fb:NOP",
            "05fc:SWAP",
            "05fd:SYSCALL[0xaf270b05]",
            "0603:NOP",
            "0604:FROMALTSTACK",
            "0605:DROP",
            "0606:RET",
            "0607:PUSH3",
            "0608:NEWARRAY",
            "0609:TOALTSTACK",
            "060a:FROMALTSTACK",
            "060b:DUP",
            "060c:TOALTSTACK",
            "060d:PUSH0(false)",
            "060e:PUSH2",
            "060f:ROLL",
            "0610:SETITEM",
            "0611:FROMALTSTACK",
            "0612:DUP",
            "0613:TOALTSTACK",
            "0614:PUSH1(true)",
            "0615:PUSH2",
            "0616:ROLL",
            "0617:SETITEM",
            "0618:DUPFROMALTSTACK",
            "0619:PUSH0(false)",
            "061a:PICKITEM",
            "061b:PUSH1(true)",
            "061c:PICKITEM",
            "061d:PUSHBYTES1[0x00]",
            "061f:CAT",
            "0620:DUPFROMALTSTACK",
            "0621:PUSH1(true)",
            "0622:PICKITEM",
            "0623:CAT",
            "0624:DUPFROMALTSTACK",
            "0625:PUSH2",
            "0626:PUSH2",
            "0627:ROLL",
            "0628:SETITEM",
            "0629:DUPFROMALTSTACK",
            "062a:PUSH0(false)",
            "062b:PICKITEM",
            "062c:PUSH0(false)",
            "062d:PICKITEM",
            "062e:DUPFROMALTSTACK",
            "062f:PUSH2",
            "0630:PICKITEM",
            "0631:NOP",
            "0632:SWAP",
            "0633:SYSCALL[0x5dabecb3]",
            "0639:NOP",
            "063a:FROMALTSTACK",
            "063b:DROP",
            "063c:RET"
        ]
    }
}
```

