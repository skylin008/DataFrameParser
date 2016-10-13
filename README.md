#DataFrameParser<br/>
用于解析带有数据校验头和数据校验尾的数据<br/>
单片机与一些外设进行数据交换时通常会带有一些数据校验头和校验尾，如单片机与某外设进行工作时，外设返回的数据如下：<br/>
0xAA 0xAA 0x04 0x80 0x02 0x00 0x02 0x7B 0xAA 0xAA 0x04 0x80 0x02 0x00 0xF6 0x87<br/>
其中 0xAA 0xAA 0x04 0x80 0x02 为数据头，后面三位为有效数据<br/>
该解析器可以从外设不断返回的数据中提取出有效数据，可以适用于所有带数据数据校验头和校验尾的数据<br/>
<br/>
使用方法：<br/>
	1 使用 parser_init() 函数初始化一个解析器<br/>
	2 使用 parser_put_data() 函数将要解析的数据添加到解析器进行解析<br/>
	3 判断解析器解析后返回的结果，如果返回 RESULT_TRUE 代表成功解析出一帧数据<br/>
	4 成功解析出数据后可以使用 parser_get_data() 函数从解析出来的数据中获取目标数据<br/>
<br/>
具体使用方法参照 main.c 文件