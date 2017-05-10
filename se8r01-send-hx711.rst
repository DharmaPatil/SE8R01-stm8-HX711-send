                                      1 ;--------------------------------------------------------
                                      2 ; File Created by SDCC : free open source ANSI-C Compiler
                                      3 ; Version 3.4.0 #8981 (Jul 11 2014) (Linux)
                                      4 ; This file was generated Wed May 10 15:24:10 2017
                                      5 ;--------------------------------------------------------
                                      6 	.module se8r01_send_hx711
                                      7 	.optsdcc -mstm8
                                      8 	
                                      9 ;--------------------------------------------------------
                                     10 ; Public variables in this module
                                     11 ;--------------------------------------------------------
                                     12 	.globl _main
                                     13 	.globl _SE8R01_Init
                                     14 	.globl _SE8R01_Analog_Init
                                     15 	.globl _SE8R01_Calibration
                                     16 	.globl _rf_switch_bank
                                     17 	.globl _init_io
                                     18 	.globl _InitializeUART
                                     19 	.globl _print_UCHAR_hex
                                     20 	.globl _UARTPrintF
                                     21 	.globl _delay
                                     22 	.globl _InitializeSystemClock
                                     23 	.globl _InitializeSPI
                                     24 	.globl _read_spi_buf
                                     25 	.globl _write_spi_buf
                                     26 	.globl _read_spi_reg
                                     27 	.globl _write_spi_reg
                                     28 	.globl _write_spi
                                     29 	.globl _delayTenMicro
                                     30 	.globl _memset
                                     31 	.globl _tx_buf
                                     32 	.globl _rx_buf
                                     33 	.globl _ADDRESS0
                                     34 	.globl _ADDRESS1
                                     35 	.globl _ADDRESS5
                                     36 	.globl _ADDRESS4
                                     37 	.globl _ADDRESS3
                                     38 	.globl _ADDRESS2
                                     39 	.globl _TX_ADDRESS
                                     40 	.globl _status
                                     41 	.globl _pip
                                     42 	.globl _signal_lv
                                     43 	.globl _newdata
                                     44 	.globl _pload_width_now
                                     45 	.globl _SE8R01_DR_500K
                                     46 	.globl _SE8R01_DR_1M
                                     47 	.globl _SE8R01_DR_2M
                                     48 	.globl _myData_pip4
                                     49 	.globl _myData_pip5
                                     50 	.globl _gtemp
                                     51 ;--------------------------------------------------------
                                     52 ; ram data
                                     53 ;--------------------------------------------------------
                                     54 	.area DATA
      000001                         55 _gtemp::
      000001                         56 	.ds 5
      000006                         57 _myData_pip5::
      000006                         58 	.ds 5
      00000B                         59 _myData_pip4::
      00000B                         60 	.ds 5
                                     61 ;--------------------------------------------------------
                                     62 ; ram data
                                     63 ;--------------------------------------------------------
                                     64 	.area INITIALIZED
      000010                         65 _SE8R01_DR_2M::
      000010                         66 	.ds 2
      000012                         67 _SE8R01_DR_1M::
      000012                         68 	.ds 2
      000014                         69 _SE8R01_DR_500K::
      000014                         70 	.ds 2
      000016                         71 _pload_width_now::
      000016                         72 	.ds 2
      000018                         73 _newdata::
      000018                         74 	.ds 2
      00001A                         75 _signal_lv::
      00001A                         76 	.ds 1
      00001B                         77 _pip::
      00001B                         78 	.ds 2
      00001D                         79 _status::
      00001D                         80 	.ds 1
      00001E                         81 _TX_ADDRESS::
      00001E                         82 	.ds 4
      000022                         83 _ADDRESS2::
      000022                         84 	.ds 1
      000023                         85 _ADDRESS3::
      000023                         86 	.ds 1
      000024                         87 _ADDRESS4::
      000024                         88 	.ds 1
      000025                         89 _ADDRESS5::
      000025                         90 	.ds 1
      000026                         91 _ADDRESS1::
      000026                         92 	.ds 4
      00002A                         93 _ADDRESS0::
      00002A                         94 	.ds 4
      00002E                         95 _rx_buf::
      00002E                         96 	.ds 32
      00004E                         97 _tx_buf::
      00004E                         98 	.ds 32
                                     99 ;--------------------------------------------------------
                                    100 ; Stack segment in internal ram 
                                    101 ;--------------------------------------------------------
                                    102 	.area	SSEG
      000000                        103 __start__stack:
      000000                        104 	.ds	1
                                    105 
                                    106 ;--------------------------------------------------------
                                    107 ; absolute external ram data
                                    108 ;--------------------------------------------------------
                                    109 	.area DABS (ABS)
                                    110 ;--------------------------------------------------------
                                    111 ; interrupt vector 
                                    112 ;--------------------------------------------------------
                                    113 	.area HOME
      008000                        114 __interrupt_vect:
      008000 82 00 80 83            115 	int s_GSINIT ;reset
      008004 82 00 00 00            116 	int 0x0000 ;trap
      008008 82 00 00 00            117 	int 0x0000 ;int0
      00800C 82 00 00 00            118 	int 0x0000 ;int1
      008010 82 00 00 00            119 	int 0x0000 ;int2
      008014 82 00 00 00            120 	int 0x0000 ;int3
      008018 82 00 00 00            121 	int 0x0000 ;int4
      00801C 82 00 00 00            122 	int 0x0000 ;int5
      008020 82 00 00 00            123 	int 0x0000 ;int6
      008024 82 00 00 00            124 	int 0x0000 ;int7
      008028 82 00 00 00            125 	int 0x0000 ;int8
      00802C 82 00 00 00            126 	int 0x0000 ;int9
      008030 82 00 00 00            127 	int 0x0000 ;int10
      008034 82 00 00 00            128 	int 0x0000 ;int11
      008038 82 00 00 00            129 	int 0x0000 ;int12
      00803C 82 00 00 00            130 	int 0x0000 ;int13
      008040 82 00 00 00            131 	int 0x0000 ;int14
      008044 82 00 00 00            132 	int 0x0000 ;int15
      008048 82 00 00 00            133 	int 0x0000 ;int16
      00804C 82 00 00 00            134 	int 0x0000 ;int17
      008050 82 00 00 00            135 	int 0x0000 ;int18
      008054 82 00 00 00            136 	int 0x0000 ;int19
      008058 82 00 00 00            137 	int 0x0000 ;int20
      00805C 82 00 00 00            138 	int 0x0000 ;int21
      008060 82 00 00 00            139 	int 0x0000 ;int22
      008064 82 00 00 00            140 	int 0x0000 ;int23
      008068 82 00 00 00            141 	int 0x0000 ;int24
      00806C 82 00 00 00            142 	int 0x0000 ;int25
      008070 82 00 00 00            143 	int 0x0000 ;int26
      008074 82 00 00 00            144 	int 0x0000 ;int27
      008078 82 00 00 00            145 	int 0x0000 ;int28
      00807C 82 00 00 00            146 	int 0x0000 ;int29
                                    147 ;--------------------------------------------------------
                                    148 ; global & static initialisations
                                    149 ;--------------------------------------------------------
                                    150 	.area HOME
                                    151 	.area GSINIT
                                    152 	.area GSFINAL
                                    153 	.area GSINIT
      008083                        154 __sdcc_gs_init_startup:
      008083                        155 __sdcc_init_data:
                                    156 ; stm8_genXINIT() start
      008083 AE 00 0F         [ 2]  157 	ldw x, #l_DATA
      008086 27 07            [ 1]  158 	jreq	00002$
      008088                        159 00001$:
      008088 72 4F 00 00      [ 1]  160 	clr (s_DATA - 1, x)
      00808C 5A               [ 2]  161 	decw x
      00808D 26 F9            [ 1]  162 	jrne	00001$
      00808F                        163 00002$:
      00808F AE 00 5E         [ 2]  164 	ldw	x, #l_INITIALIZER
      008092 27 09            [ 1]  165 	jreq	00004$
      008094                        166 00003$:
      008094 D6 89 5B         [ 1]  167 	ld	a, (s_INITIALIZER - 1, x)
      008097 D7 00 0F         [ 1]  168 	ld	(s_INITIALIZED - 1, x), a
      00809A 5A               [ 2]  169 	decw	x
      00809B 26 F7            [ 1]  170 	jrne	00003$
      00809D                        171 00004$:
                                    172 ; stm8_genXINIT() end
                                    173 	.area GSFINAL
      00809D CC 80 80         [ 2]  174 	jp	__sdcc_program_startup
                                    175 ;--------------------------------------------------------
                                    176 ; Home
                                    177 ;--------------------------------------------------------
                                    178 	.area HOME
                                    179 	.area HOME
      008080                        180 __sdcc_program_startup:
      008080 CC 87 8C         [ 2]  181 	jp	_main
                                    182 ;	return from main will return to caller
                                    183 ;--------------------------------------------------------
                                    184 ; code
                                    185 ;--------------------------------------------------------
                                    186 	.area CODE
                                    187 ;	se8r01-send-hx711.c: 33: void delayTenMicro (void) {
                                    188 ;	-----------------------------------------
                                    189 ;	 function delayTenMicro
                                    190 ;	-----------------------------------------
      0080A0                        191 _delayTenMicro:
                                    192 ;	se8r01-send-hx711.c: 35: for (a = 0; a < 50; ++a)
      0080A0 A6 32            [ 1]  193 	ld	a, #0x32
      0080A2                        194 00104$:
                                    195 ;	se8r01-send-hx711.c: 36: __asm__("nop");
      0080A2 9D               [ 1]  196 	nop
      0080A3 4A               [ 1]  197 	dec	a
                                    198 ;	se8r01-send-hx711.c: 35: for (a = 0; a < 50; ++a)
      0080A4 4D               [ 1]  199 	tnz	a
      0080A5 26 FB            [ 1]  200 	jrne	00104$
      0080A7 81               [ 4]  201 	ret
                                    202 ;	se8r01-send-hx711.c: 38: UCHAR write_spi (UCHAR value) {
                                    203 ;	-----------------------------------------
                                    204 ;	 function write_spi
                                    205 ;	-----------------------------------------
      0080A8                        206 _write_spi:
                                    207 ;	se8r01-send-hx711.c: 40: delayTenMicro ();
      0080A8 CD 80 A0         [ 4]  208 	call	_delayTenMicro
                                    209 ;	se8r01-send-hx711.c: 41: SPI_DR = value;
      0080AB AE 52 04         [ 2]  210 	ldw	x, #0x5204
      0080AE 7B 03            [ 1]  211 	ld	a, (0x03, sp)
      0080B0 F7               [ 1]  212 	ld	(x), a
                                    213 ;	se8r01-send-hx711.c: 42: delayTenMicro ();
      0080B1 CD 80 A0         [ 4]  214 	call	_delayTenMicro
                                    215 ;	se8r01-send-hx711.c: 43: while ((SPI_SR & TXE) == 0);
      0080B4                        216 00101$:
      0080B4 AE 52 03         [ 2]  217 	ldw	x, #0x5203
      0080B7 F6               [ 1]  218 	ld	a, (x)
      0080B8 A5 02            [ 1]  219 	bcp	a, #0x02
      0080BA 27 F8            [ 1]  220 	jreq	00101$
                                    221 ;	se8r01-send-hx711.c: 44: delayTenMicro ();
      0080BC CD 80 A0         [ 4]  222 	call	_delayTenMicro
                                    223 ;	se8r01-send-hx711.c: 45: while ((SPI_SR & RXNE) == 0);
      0080BF                        224 00104$:
      0080BF AE 52 03         [ 2]  225 	ldw	x, #0x5203
      0080C2 F6               [ 1]  226 	ld	a, (x)
      0080C3 44               [ 1]  227 	srl	a
      0080C4 24 F9            [ 1]  228 	jrnc	00104$
                                    229 ;	se8r01-send-hx711.c: 46: delayTenMicro ();
      0080C6 CD 80 A0         [ 4]  230 	call	_delayTenMicro
                                    231 ;	se8r01-send-hx711.c: 47: ret = SPI_DR;
      0080C9 AE 52 04         [ 2]  232 	ldw	x, #0x5204
      0080CC F6               [ 1]  233 	ld	a, (x)
                                    234 ;	se8r01-send-hx711.c: 48: return (ret);
      0080CD 81               [ 4]  235 	ret
                                    236 ;	se8r01-send-hx711.c: 50: UCHAR write_spi_reg (UCHAR reg, UCHAR value) {
                                    237 ;	-----------------------------------------
                                    238 ;	 function write_spi_reg
                                    239 ;	-----------------------------------------
      0080CE                        240 _write_spi_reg:
      0080CE 88               [ 1]  241 	push	a
                                    242 ;	se8r01-send-hx711.c: 52: PC_ODR &= ~(1 << CSN);
      0080CF AE 50 0A         [ 2]  243 	ldw	x, #0x500a
      0080D2 F6               [ 1]  244 	ld	a, (x)
      0080D3 A4 F7            [ 1]  245 	and	a, #0xf7
      0080D5 F7               [ 1]  246 	ld	(x), a
                                    247 ;	se8r01-send-hx711.c: 53: ret = write_spi (reg);
      0080D6 7B 04            [ 1]  248 	ld	a, (0x04, sp)
      0080D8 88               [ 1]  249 	push	a
      0080D9 CD 80 A8         [ 4]  250 	call	_write_spi
      0080DC 5B 01            [ 2]  251 	addw	sp, #1
      0080DE 6B 01            [ 1]  252 	ld	(0x01, sp), a
                                    253 ;	se8r01-send-hx711.c: 54: if (reg != NOP && reg != FLUSH_RX && reg != FLUSH_TX)
      0080E0 7B 04            [ 1]  254 	ld	a, (0x04, sp)
      0080E2 A1 FF            [ 1]  255 	cp	a, #0xff
      0080E4 27 15            [ 1]  256 	jreq	00102$
      0080E6 7B 04            [ 1]  257 	ld	a, (0x04, sp)
      0080E8 A1 E2            [ 1]  258 	cp	a, #0xe2
      0080EA 27 0F            [ 1]  259 	jreq	00102$
      0080EC 7B 04            [ 1]  260 	ld	a, (0x04, sp)
      0080EE A1 E1            [ 1]  261 	cp	a, #0xe1
      0080F0 27 09            [ 1]  262 	jreq	00102$
                                    263 ;	se8r01-send-hx711.c: 55: write_spi (value);
      0080F2 7B 05            [ 1]  264 	ld	a, (0x05, sp)
      0080F4 88               [ 1]  265 	push	a
      0080F5 CD 80 A8         [ 4]  266 	call	_write_spi
      0080F8 84               [ 1]  267 	pop	a
      0080F9 20 03            [ 2]  268 	jra	00103$
      0080FB                        269 00102$:
                                    270 ;	se8r01-send-hx711.c: 57: delayTenMicro ();
      0080FB CD 80 A0         [ 4]  271 	call	_delayTenMicro
      0080FE                        272 00103$:
                                    273 ;	se8r01-send-hx711.c: 58: PC_ODR |= (1 << CSN);
      0080FE AE 50 0A         [ 2]  274 	ldw	x, #0x500a
      008101 F6               [ 1]  275 	ld	a, (x)
      008102 AA 08            [ 1]  276 	or	a, #0x08
      008104 F7               [ 1]  277 	ld	(x), a
                                    278 ;	se8r01-send-hx711.c: 59: return (ret);
      008105 7B 01            [ 1]  279 	ld	a, (0x01, sp)
      008107 5B 01            [ 2]  280 	addw	sp, #1
      008109 81               [ 4]  281 	ret
                                    282 ;	se8r01-send-hx711.c: 61: UCHAR read_spi_reg (UCHAR reg) {
                                    283 ;	-----------------------------------------
                                    284 ;	 function read_spi_reg
                                    285 ;	-----------------------------------------
      00810A                        286 _read_spi_reg:
      00810A 88               [ 1]  287 	push	a
                                    288 ;	se8r01-send-hx711.c: 63: PC_ODR &= ~(1 << CSN);
      00810B AE 50 0A         [ 2]  289 	ldw	x, #0x500a
      00810E F6               [ 1]  290 	ld	a, (x)
      00810F A4 F7            [ 1]  291 	and	a, #0xf7
      008111 F7               [ 1]  292 	ld	(x), a
                                    293 ;	se8r01-send-hx711.c: 64: ret = write_spi (reg);
      008112 7B 04            [ 1]  294 	ld	a, (0x04, sp)
      008114 88               [ 1]  295 	push	a
      008115 CD 80 A8         [ 4]  296 	call	_write_spi
      008118 5B 01            [ 2]  297 	addw	sp, #1
      00811A 6B 01            [ 1]  298 	ld	(0x01, sp), a
                                    299 ;	se8r01-send-hx711.c: 65: if (reg != NOP && reg != FLUSH_RX && reg != FLUSH_TX)
      00811C 7B 04            [ 1]  300 	ld	a, (0x04, sp)
      00811E A1 FF            [ 1]  301 	cp	a, #0xff
      008120 27 17            [ 1]  302 	jreq	00102$
      008122 7B 04            [ 1]  303 	ld	a, (0x04, sp)
      008124 A1 E2            [ 1]  304 	cp	a, #0xe2
      008126 27 11            [ 1]  305 	jreq	00102$
      008128 7B 04            [ 1]  306 	ld	a, (0x04, sp)
      00812A A1 E1            [ 1]  307 	cp	a, #0xe1
      00812C 27 0B            [ 1]  308 	jreq	00102$
                                    309 ;	se8r01-send-hx711.c: 66: ret = write_spi (NOP);
      00812E 4B FF            [ 1]  310 	push	#0xff
      008130 CD 80 A8         [ 4]  311 	call	_write_spi
      008133 5B 01            [ 2]  312 	addw	sp, #1
      008135 6B 01            [ 1]  313 	ld	(0x01, sp), a
      008137 20 03            [ 2]  314 	jra	00103$
      008139                        315 00102$:
                                    316 ;	se8r01-send-hx711.c: 68: delayTenMicro ();
      008139 CD 80 A0         [ 4]  317 	call	_delayTenMicro
      00813C                        318 00103$:
                                    319 ;	se8r01-send-hx711.c: 69: PC_ODR |= (1 << CSN);
      00813C AE 50 0A         [ 2]  320 	ldw	x, #0x500a
      00813F F6               [ 1]  321 	ld	a, (x)
      008140 AA 08            [ 1]  322 	or	a, #0x08
      008142 F7               [ 1]  323 	ld	(x), a
                                    324 ;	se8r01-send-hx711.c: 70: return (ret);
      008143 7B 01            [ 1]  325 	ld	a, (0x01, sp)
      008145 5B 01            [ 2]  326 	addw	sp, #1
      008147 81               [ 4]  327 	ret
                                    328 ;	se8r01-send-hx711.c: 72: UCHAR write_spi_buf (UCHAR reg, UCHAR *array, UCHAR len) {
                                    329 ;	-----------------------------------------
                                    330 ;	 function write_spi_buf
                                    331 ;	-----------------------------------------
      008148                        332 _write_spi_buf:
      008148 52 02            [ 2]  333 	sub	sp, #2
                                    334 ;	se8r01-send-hx711.c: 74: PC_ODR &= ~(1 << CSN);
      00814A AE 50 0A         [ 2]  335 	ldw	x, #0x500a
      00814D F6               [ 1]  336 	ld	a, (x)
      00814E A4 F7            [ 1]  337 	and	a, #0xf7
      008150 F7               [ 1]  338 	ld	(x), a
                                    339 ;	se8r01-send-hx711.c: 75: ret = write_spi (reg);
      008151 7B 05            [ 1]  340 	ld	a, (0x05, sp)
      008153 88               [ 1]  341 	push	a
      008154 CD 80 A8         [ 4]  342 	call	_write_spi
      008157 5B 01            [ 2]  343 	addw	sp, #1
      008159 6B 02            [ 1]  344 	ld	(0x02, sp), a
                                    345 ;	se8r01-send-hx711.c: 76: for (n = 0; n < len; ++n)
      00815B 0F 01            [ 1]  346 	clr	(0x01, sp)
      00815D                        347 00103$:
      00815D 7B 01            [ 1]  348 	ld	a, (0x01, sp)
      00815F 11 08            [ 1]  349 	cp	a, (0x08, sp)
      008161 24 11            [ 1]  350 	jrnc	00101$
                                    351 ;	se8r01-send-hx711.c: 77: write_spi (array[n]);
      008163 5F               [ 1]  352 	clrw	x
      008164 7B 01            [ 1]  353 	ld	a, (0x01, sp)
      008166 97               [ 1]  354 	ld	xl, a
      008167 72 FB 06         [ 2]  355 	addw	x, (0x06, sp)
      00816A F6               [ 1]  356 	ld	a, (x)
      00816B 88               [ 1]  357 	push	a
      00816C CD 80 A8         [ 4]  358 	call	_write_spi
      00816F 84               [ 1]  359 	pop	a
                                    360 ;	se8r01-send-hx711.c: 76: for (n = 0; n < len; ++n)
      008170 0C 01            [ 1]  361 	inc	(0x01, sp)
      008172 20 E9            [ 2]  362 	jra	00103$
      008174                        363 00101$:
                                    364 ;	se8r01-send-hx711.c: 78: PC_ODR |= (1 << CSN);
      008174 AE 50 0A         [ 2]  365 	ldw	x, #0x500a
      008177 F6               [ 1]  366 	ld	a, (x)
      008178 AA 08            [ 1]  367 	or	a, #0x08
      00817A F7               [ 1]  368 	ld	(x), a
                                    369 ;	se8r01-send-hx711.c: 79: return (ret);
      00817B 7B 02            [ 1]  370 	ld	a, (0x02, sp)
      00817D 5B 02            [ 2]  371 	addw	sp, #2
      00817F 81               [ 4]  372 	ret
                                    373 ;	se8r01-send-hx711.c: 81: UCHAR read_spi_buf (UCHAR reg, UCHAR *array, UCHAR len) {
                                    374 ;	-----------------------------------------
                                    375 ;	 function read_spi_buf
                                    376 ;	-----------------------------------------
      008180                        377 _read_spi_buf:
      008180 52 02            [ 2]  378 	sub	sp, #2
                                    379 ;	se8r01-send-hx711.c: 83: PC_ODR &= ~(1 << CSN);
      008182 AE 50 0A         [ 2]  380 	ldw	x, #0x500a
      008185 F6               [ 1]  381 	ld	a, (x)
      008186 A4 F7            [ 1]  382 	and	a, #0xf7
      008188 F7               [ 1]  383 	ld	(x), a
                                    384 ;	se8r01-send-hx711.c: 84: ret = write_spi (reg);
      008189 7B 05            [ 1]  385 	ld	a, (0x05, sp)
      00818B 88               [ 1]  386 	push	a
      00818C CD 80 A8         [ 4]  387 	call	_write_spi
      00818F 5B 01            [ 2]  388 	addw	sp, #1
      008191 6B 01            [ 1]  389 	ld	(0x01, sp), a
                                    390 ;	se8r01-send-hx711.c: 85: for (n = 0; n < len; ++n)
      008193 0F 02            [ 1]  391 	clr	(0x02, sp)
      008195                        392 00103$:
      008195 7B 02            [ 1]  393 	ld	a, (0x02, sp)
      008197 11 08            [ 1]  394 	cp	a, (0x08, sp)
      008199 24 15            [ 1]  395 	jrnc	00101$
                                    396 ;	se8r01-send-hx711.c: 86: array[n] = write_spi (NOP);
      00819B 5F               [ 1]  397 	clrw	x
      00819C 7B 02            [ 1]  398 	ld	a, (0x02, sp)
      00819E 97               [ 1]  399 	ld	xl, a
      00819F 72 FB 06         [ 2]  400 	addw	x, (0x06, sp)
      0081A2 89               [ 2]  401 	pushw	x
      0081A3 4B FF            [ 1]  402 	push	#0xff
      0081A5 CD 80 A8         [ 4]  403 	call	_write_spi
      0081A8 5B 01            [ 2]  404 	addw	sp, #1
      0081AA 85               [ 2]  405 	popw	x
      0081AB F7               [ 1]  406 	ld	(x), a
                                    407 ;	se8r01-send-hx711.c: 85: for (n = 0; n < len; ++n)
      0081AC 0C 02            [ 1]  408 	inc	(0x02, sp)
      0081AE 20 E5            [ 2]  409 	jra	00103$
      0081B0                        410 00101$:
                                    411 ;	se8r01-send-hx711.c: 87: PC_ODR |= (1 << CSN);
      0081B0 AE 50 0A         [ 2]  412 	ldw	x, #0x500a
      0081B3 F6               [ 1]  413 	ld	a, (x)
      0081B4 AA 08            [ 1]  414 	or	a, #0x08
      0081B6 F7               [ 1]  415 	ld	(x), a
                                    416 ;	se8r01-send-hx711.c: 88: return (ret);
      0081B7 7B 01            [ 1]  417 	ld	a, (0x01, sp)
      0081B9 5B 02            [ 2]  418 	addw	sp, #2
      0081BB 81               [ 4]  419 	ret
                                    420 ;	se8r01-send-hx711.c: 90: void InitializeSPI () {
                                    421 ;	-----------------------------------------
                                    422 ;	 function InitializeSPI
                                    423 ;	-----------------------------------------
      0081BC                        424 _InitializeSPI:
                                    425 ;	se8r01-send-hx711.c: 91: SPI_CR1 = MSBFIRST | SPI_ENABLE | BR_DIV256 | MASTER | CPOL0 | CPHA0;
      0081BC AE 52 00         [ 2]  426 	ldw	x, #0x5200
      0081BF A6 7C            [ 1]  427 	ld	a, #0x7c
      0081C1 F7               [ 1]  428 	ld	(x), a
                                    429 ;	se8r01-send-hx711.c: 92: SPI_CR2 = BDM_2LINE | CRCEN_OFF | CRCNEXT_TXBUF | FULL_DUPLEX | SSM_DISABLE;
      0081C2 AE 52 01         [ 2]  430 	ldw	x, #0x5201
      0081C5 7F               [ 1]  431 	clr	(x)
                                    432 ;	se8r01-send-hx711.c: 93: SPI_ICR = TXIE_MASKED | RXIE_MASKED | ERRIE_MASKED | WKIE_MASKED;
      0081C6 AE 52 02         [ 2]  433 	ldw	x, #0x5202
      0081C9 7F               [ 1]  434 	clr	(x)
                                    435 ;	se8r01-send-hx711.c: 94: PC_DDR = (1 << PC3) | (1 << PC4); // output mode
      0081CA AE 50 0C         [ 2]  436 	ldw	x, #0x500c
      0081CD A6 18            [ 1]  437 	ld	a, #0x18
      0081CF F7               [ 1]  438 	ld	(x), a
                                    439 ;	se8r01-send-hx711.c: 95: PC_CR1 = (1 << PC3) | (1 << PC4); // push-pull
      0081D0 AE 50 0D         [ 2]  440 	ldw	x, #0x500d
      0081D3 A6 18            [ 1]  441 	ld	a, #0x18
      0081D5 F7               [ 1]  442 	ld	(x), a
                                    443 ;	se8r01-send-hx711.c: 96: PC_CR2 = (1 << PC3) | (1 << PC4); // up to 10MHz speed
      0081D6 AE 50 0E         [ 2]  444 	ldw	x, #0x500e
      0081D9 A6 18            [ 1]  445 	ld	a, #0x18
      0081DB F7               [ 1]  446 	ld	(x), a
                                    447 ;	se8r01-send-hx711.c: 98: PC_ODR &= ~(1 << CE);
      0081DC AE 50 0A         [ 2]  448 	ldw	x, #0x500a
      0081DF F6               [ 1]  449 	ld	a, (x)
      0081E0 A4 EF            [ 1]  450 	and	a, #0xef
      0081E2 F7               [ 1]  451 	ld	(x), a
      0081E3 81               [ 4]  452 	ret
                                    453 ;	se8r01-send-hx711.c: 100: void InitializeSystemClock() {
                                    454 ;	-----------------------------------------
                                    455 ;	 function InitializeSystemClock
                                    456 ;	-----------------------------------------
      0081E4                        457 _InitializeSystemClock:
                                    458 ;	se8r01-send-hx711.c: 101: CLK_ICKR = 0;                       //  Reset the Internal Clock Register.
      0081E4 AE 50 C0         [ 2]  459 	ldw	x, #0x50c0
      0081E7 7F               [ 1]  460 	clr	(x)
                                    461 ;	se8r01-send-hx711.c: 102: CLK_ICKR = CLK_HSIEN;               //  Enable the HSI.
      0081E8 AE 50 C0         [ 2]  462 	ldw	x, #0x50c0
      0081EB A6 01            [ 1]  463 	ld	a, #0x01
      0081ED F7               [ 1]  464 	ld	(x), a
                                    465 ;	se8r01-send-hx711.c: 103: CLK_ECKR = 0;                       //  Disable the external clock.
      0081EE AE 50 C1         [ 2]  466 	ldw	x, #0x50c1
      0081F1 7F               [ 1]  467 	clr	(x)
                                    468 ;	se8r01-send-hx711.c: 104: while ((CLK_ICKR & CLK_HSIRDY) == 0);       //  Wait for the HSI to be ready for use.
      0081F2                        469 00101$:
      0081F2 AE 50 C0         [ 2]  470 	ldw	x, #0x50c0
      0081F5 F6               [ 1]  471 	ld	a, (x)
      0081F6 A5 02            [ 1]  472 	bcp	a, #0x02
      0081F8 27 F8            [ 1]  473 	jreq	00101$
                                    474 ;	se8r01-send-hx711.c: 105: CLK_CKDIVR = 0;                     //  Ensure the clocks are running at full speed.
      0081FA AE 50 C6         [ 2]  475 	ldw	x, #0x50c6
      0081FD 7F               [ 1]  476 	clr	(x)
                                    477 ;	se8r01-send-hx711.c: 106: CLK_PCKENR1 = 0xff;                 //  Enable all peripheral clocks.
      0081FE AE 50 C7         [ 2]  478 	ldw	x, #0x50c7
      008201 A6 FF            [ 1]  479 	ld	a, #0xff
      008203 F7               [ 1]  480 	ld	(x), a
                                    481 ;	se8r01-send-hx711.c: 107: CLK_PCKENR2 = 0xff;                 //  Ditto.
      008204 AE 50 CA         [ 2]  482 	ldw	x, #0x50ca
      008207 A6 FF            [ 1]  483 	ld	a, #0xff
      008209 F7               [ 1]  484 	ld	(x), a
                                    485 ;	se8r01-send-hx711.c: 108: CLK_CCOR = 0;                       //  Turn off CCO.
      00820A AE 50 C9         [ 2]  486 	ldw	x, #0x50c9
      00820D 7F               [ 1]  487 	clr	(x)
                                    488 ;	se8r01-send-hx711.c: 109: CLK_HSITRIMR = 0;                   //  Turn off any HSIU trimming.
      00820E AE 50 CC         [ 2]  489 	ldw	x, #0x50cc
      008211 7F               [ 1]  490 	clr	(x)
                                    491 ;	se8r01-send-hx711.c: 110: CLK_SWIMCCR = 0;                    //  Set SWIM to run at clock / 2.
      008212 AE 50 CD         [ 2]  492 	ldw	x, #0x50cd
      008215 7F               [ 1]  493 	clr	(x)
                                    494 ;	se8r01-send-hx711.c: 111: CLK_SWR = 0xe1;                     //  Use HSI as the clock source.
      008216 AE 50 C4         [ 2]  495 	ldw	x, #0x50c4
      008219 A6 E1            [ 1]  496 	ld	a, #0xe1
      00821B F7               [ 1]  497 	ld	(x), a
                                    498 ;	se8r01-send-hx711.c: 112: CLK_SWCR = 0;                       //  Reset the clock switch control register.
      00821C AE 50 C5         [ 2]  499 	ldw	x, #0x50c5
      00821F 7F               [ 1]  500 	clr	(x)
                                    501 ;	se8r01-send-hx711.c: 113: CLK_SWCR = CLK_SWEN;                //  Enable switching.
      008220 AE 50 C5         [ 2]  502 	ldw	x, #0x50c5
      008223 A6 02            [ 1]  503 	ld	a, #0x02
      008225 F7               [ 1]  504 	ld	(x), a
                                    505 ;	se8r01-send-hx711.c: 114: while ((CLK_SWCR & CLK_SWBSY) != 0);        //  Pause while the clock switch is busy.
      008226                        506 00104$:
      008226 AE 50 C5         [ 2]  507 	ldw	x, #0x50c5
      008229 F6               [ 1]  508 	ld	a, (x)
      00822A 44               [ 1]  509 	srl	a
      00822B 25 F9            [ 1]  510 	jrc	00104$
      00822D 81               [ 4]  511 	ret
                                    512 ;	se8r01-send-hx711.c: 116: void delay (int time_ms) {
                                    513 ;	-----------------------------------------
                                    514 ;	 function delay
                                    515 ;	-----------------------------------------
      00822E                        516 _delay:
      00822E 52 0A            [ 2]  517 	sub	sp, #10
                                    518 ;	se8r01-send-hx711.c: 118: for (x = 0; x < 1036*time_ms; ++x)
      008230 5F               [ 1]  519 	clrw	x
      008231 1F 03            [ 2]  520 	ldw	(0x03, sp), x
      008233 1F 01            [ 2]  521 	ldw	(0x01, sp), x
      008235 1E 0D            [ 2]  522 	ldw	x, (0x0d, sp)
      008237 89               [ 2]  523 	pushw	x
      008238 4B 0C            [ 1]  524 	push	#0x0c
      00823A 4B 04            [ 1]  525 	push	#0x04
      00823C CD 88 E7         [ 4]  526 	call	__mulint
      00823F 5B 04            [ 2]  527 	addw	sp, #4
      008241 1F 09            [ 2]  528 	ldw	(0x09, sp), x
      008243                        529 00103$:
      008243 16 09            [ 2]  530 	ldw	y, (0x09, sp)
      008245 17 07            [ 2]  531 	ldw	(0x07, sp), y
      008247 7B 07            [ 1]  532 	ld	a, (0x07, sp)
      008249 49               [ 1]  533 	rlc	a
      00824A 4F               [ 1]  534 	clr	a
      00824B A2 00            [ 1]  535 	sbc	a, #0x00
      00824D 6B 06            [ 1]  536 	ld	(0x06, sp), a
      00824F 6B 05            [ 1]  537 	ld	(0x05, sp), a
      008251 1E 03            [ 2]  538 	ldw	x, (0x03, sp)
      008253 13 07            [ 2]  539 	cpw	x, (0x07, sp)
      008255 7B 02            [ 1]  540 	ld	a, (0x02, sp)
      008257 12 06            [ 1]  541 	sbc	a, (0x06, sp)
      008259 7B 01            [ 1]  542 	ld	a, (0x01, sp)
      00825B 12 05            [ 1]  543 	sbc	a, (0x05, sp)
      00825D 2E 17            [ 1]  544 	jrsge	00105$
                                    545 ;	se8r01-send-hx711.c: 119: __asm__("nop");
      00825F 9D               [ 1]  546 	nop
                                    547 ;	se8r01-send-hx711.c: 118: for (x = 0; x < 1036*time_ms; ++x)
      008260 16 03            [ 2]  548 	ldw	y, (0x03, sp)
      008262 72 A9 00 01      [ 2]  549 	addw	y, #0x0001
      008266 7B 02            [ 1]  550 	ld	a, (0x02, sp)
      008268 A9 00            [ 1]  551 	adc	a, #0x00
      00826A 97               [ 1]  552 	ld	xl, a
      00826B 7B 01            [ 1]  553 	ld	a, (0x01, sp)
      00826D A9 00            [ 1]  554 	adc	a, #0x00
      00826F 95               [ 1]  555 	ld	xh, a
      008270 17 03            [ 2]  556 	ldw	(0x03, sp), y
      008272 1F 01            [ 2]  557 	ldw	(0x01, sp), x
      008274 20 CD            [ 2]  558 	jra	00103$
      008276                        559 00105$:
      008276 5B 0A            [ 2]  560 	addw	sp, #10
      008278 81               [ 4]  561 	ret
                                    562 ;	se8r01-send-hx711.c: 124: void UARTPrintF (char *message) {
                                    563 ;	-----------------------------------------
                                    564 ;	 function UARTPrintF
                                    565 ;	-----------------------------------------
      008279                        566 _UARTPrintF:
                                    567 ;	se8r01-send-hx711.c: 125: char *ch = message;
      008279 16 03            [ 2]  568 	ldw	y, (0x03, sp)
                                    569 ;	se8r01-send-hx711.c: 126: while (*ch) {
      00827B                        570 00104$:
      00827B 90 F6            [ 1]  571 	ld	a, (y)
      00827D 4D               [ 1]  572 	tnz	a
      00827E 27 0F            [ 1]  573 	jreq	00107$
                                    574 ;	se8r01-send-hx711.c: 127: UART1_DR = (unsigned char) *ch;     //  Put the next character into the data transmission register.
      008280 AE 52 31         [ 2]  575 	ldw	x, #0x5231
      008283 F7               [ 1]  576 	ld	(x), a
                                    577 ;	se8r01-send-hx711.c: 128: while ((UART1_SR & SR_TXE) == 0);   //  Wait for transmission to complete.
      008284                        578 00101$:
      008284 AE 52 30         [ 2]  579 	ldw	x, #0x5230
      008287 F6               [ 1]  580 	ld	a, (x)
      008288 48               [ 1]  581 	sll	a
      008289 24 F9            [ 1]  582 	jrnc	00101$
                                    583 ;	se8r01-send-hx711.c: 129: ch++;                               //  Grab the next character.
      00828B 90 5C            [ 2]  584 	incw	y
      00828D 20 EC            [ 2]  585 	jra	00104$
      00828F                        586 00107$:
      00828F 81               [ 4]  587 	ret
                                    588 ;	se8r01-send-hx711.c: 132: void print_UCHAR_hex (unsigned char buffer) {
                                    589 ;	-----------------------------------------
                                    590 ;	 function print_UCHAR_hex
                                    591 ;	-----------------------------------------
      008290                        592 _print_UCHAR_hex:
      008290 52 0C            [ 2]  593 	sub	sp, #12
                                    594 ;	se8r01-send-hx711.c: 135: a = (buffer >> 4);
      008292 7B 0F            [ 1]  595 	ld	a, (0x0f, sp)
      008294 4E               [ 1]  596 	swap	a
      008295 A4 0F            [ 1]  597 	and	a, #0x0f
      008297 5F               [ 1]  598 	clrw	x
      008298 97               [ 1]  599 	ld	xl, a
                                    600 ;	se8r01-send-hx711.c: 136: if (a > 9)
      008299 A3 00 09         [ 2]  601 	cpw	x, #0x0009
      00829C 2D 07            [ 1]  602 	jrsle	00102$
                                    603 ;	se8r01-send-hx711.c: 137: a = a + 'a' - 10;
      00829E 1C 00 57         [ 2]  604 	addw	x, #0x0057
      0082A1 1F 03            [ 2]  605 	ldw	(0x03, sp), x
      0082A3 20 05            [ 2]  606 	jra	00103$
      0082A5                        607 00102$:
                                    608 ;	se8r01-send-hx711.c: 139: a += '0'; 
      0082A5 1C 00 30         [ 2]  609 	addw	x, #0x0030
      0082A8 1F 03            [ 2]  610 	ldw	(0x03, sp), x
      0082AA                        611 00103$:
                                    612 ;	se8r01-send-hx711.c: 140: b = buffer & 0x0f;
      0082AA 7B 0F            [ 1]  613 	ld	a, (0x0f, sp)
      0082AC A4 0F            [ 1]  614 	and	a, #0x0f
      0082AE 5F               [ 1]  615 	clrw	x
      0082AF 97               [ 1]  616 	ld	xl, a
                                    617 ;	se8r01-send-hx711.c: 141: if (b > 9)
      0082B0 A3 00 09         [ 2]  618 	cpw	x, #0x0009
      0082B3 2D 07            [ 1]  619 	jrsle	00105$
                                    620 ;	se8r01-send-hx711.c: 142: b = b + 'a' - 10;
      0082B5 1C 00 57         [ 2]  621 	addw	x, #0x0057
      0082B8 1F 01            [ 2]  622 	ldw	(0x01, sp), x
      0082BA 20 05            [ 2]  623 	jra	00106$
      0082BC                        624 00105$:
                                    625 ;	se8r01-send-hx711.c: 144: b += '0'; 
      0082BC 1C 00 30         [ 2]  626 	addw	x, #0x0030
      0082BF 1F 01            [ 2]  627 	ldw	(0x01, sp), x
      0082C1                        628 00106$:
                                    629 ;	se8r01-send-hx711.c: 145: message[0] = a;
      0082C1 90 96            [ 1]  630 	ldw	y, sp
      0082C3 72 A9 00 05      [ 2]  631 	addw	y, #5
      0082C7 7B 04            [ 1]  632 	ld	a, (0x04, sp)
      0082C9 90 F7            [ 1]  633 	ld	(y), a
                                    634 ;	se8r01-send-hx711.c: 146: message[1] = b;
      0082CB 93               [ 1]  635 	ldw	x, y
      0082CC 5C               [ 2]  636 	incw	x
      0082CD 7B 02            [ 1]  637 	ld	a, (0x02, sp)
      0082CF F7               [ 1]  638 	ld	(x), a
                                    639 ;	se8r01-send-hx711.c: 147: message[2] = 0;
      0082D0 93               [ 1]  640 	ldw	x, y
      0082D1 5C               [ 2]  641 	incw	x
      0082D2 5C               [ 2]  642 	incw	x
      0082D3 7F               [ 1]  643 	clr	(x)
                                    644 ;	se8r01-send-hx711.c: 148: UARTPrintF (message);
      0082D4 90 89            [ 2]  645 	pushw	y
      0082D6 CD 82 79         [ 4]  646 	call	_UARTPrintF
      0082D9 5B 02            [ 2]  647 	addw	sp, #2
      0082DB 5B 0C            [ 2]  648 	addw	sp, #12
      0082DD 81               [ 4]  649 	ret
                                    650 ;	se8r01-send-hx711.c: 151: void InitializeUART() {
                                    651 ;	-----------------------------------------
                                    652 ;	 function InitializeUART
                                    653 ;	-----------------------------------------
      0082DE                        654 _InitializeUART:
                                    655 ;	se8r01-send-hx711.c: 161: UART1_CR1 = 0;
      0082DE AE 52 34         [ 2]  656 	ldw	x, #0x5234
      0082E1 7F               [ 1]  657 	clr	(x)
                                    658 ;	se8r01-send-hx711.c: 162: UART1_CR2 = 0;
      0082E2 AE 52 35         [ 2]  659 	ldw	x, #0x5235
      0082E5 7F               [ 1]  660 	clr	(x)
                                    661 ;	se8r01-send-hx711.c: 163: UART1_CR4 = 0;
      0082E6 AE 52 37         [ 2]  662 	ldw	x, #0x5237
      0082E9 7F               [ 1]  663 	clr	(x)
                                    664 ;	se8r01-send-hx711.c: 164: UART1_CR3 = 0;
      0082EA AE 52 36         [ 2]  665 	ldw	x, #0x5236
      0082ED 7F               [ 1]  666 	clr	(x)
                                    667 ;	se8r01-send-hx711.c: 165: UART1_CR5 = 0;
      0082EE AE 52 38         [ 2]  668 	ldw	x, #0x5238
      0082F1 7F               [ 1]  669 	clr	(x)
                                    670 ;	se8r01-send-hx711.c: 166: UART1_GTR = 0;
      0082F2 AE 52 39         [ 2]  671 	ldw	x, #0x5239
      0082F5 7F               [ 1]  672 	clr	(x)
                                    673 ;	se8r01-send-hx711.c: 167: UART1_PSCR = 0;
      0082F6 AE 52 3A         [ 2]  674 	ldw	x, #0x523a
      0082F9 7F               [ 1]  675 	clr	(x)
                                    676 ;	se8r01-send-hx711.c: 171: UNSET (UART1_CR1, CR1_M);        //  8 Data bits.
      0082FA AE 52 34         [ 2]  677 	ldw	x, #0x5234
      0082FD F6               [ 1]  678 	ld	a, (x)
      0082FE A4 EF            [ 1]  679 	and	a, #0xef
      008300 F7               [ 1]  680 	ld	(x), a
                                    681 ;	se8r01-send-hx711.c: 172: UNSET (UART1_CR1, CR1_PCEN);     //  Disable parity.
      008301 AE 52 34         [ 2]  682 	ldw	x, #0x5234
      008304 F6               [ 1]  683 	ld	a, (x)
      008305 A4 FB            [ 1]  684 	and	a, #0xfb
      008307 F7               [ 1]  685 	ld	(x), a
                                    686 ;	se8r01-send-hx711.c: 173: UNSET (UART1_CR3, CR3_STOPH);    //  1 stop bit.
      008308 AE 52 36         [ 2]  687 	ldw	x, #0x5236
      00830B F6               [ 1]  688 	ld	a, (x)
      00830C A4 DF            [ 1]  689 	and	a, #0xdf
      00830E F7               [ 1]  690 	ld	(x), a
                                    691 ;	se8r01-send-hx711.c: 174: UNSET (UART1_CR3, CR3_STOPL);    //  1 stop bit.
      00830F AE 52 36         [ 2]  692 	ldw	x, #0x5236
      008312 F6               [ 1]  693 	ld	a, (x)
      008313 A4 EF            [ 1]  694 	and	a, #0xef
      008315 F7               [ 1]  695 	ld	(x), a
                                    696 ;	se8r01-send-hx711.c: 175: UART1_BRR2 = 0x0a;      //  Set the baud rate registers to 115200 baud
      008316 AE 52 33         [ 2]  697 	ldw	x, #0x5233
      008319 A6 0A            [ 1]  698 	ld	a, #0x0a
      00831B F7               [ 1]  699 	ld	(x), a
                                    700 ;	se8r01-send-hx711.c: 176: UART1_BRR1 = 0x08;      //  based upon a 16 MHz system clock.
      00831C AE 52 32         [ 2]  701 	ldw	x, #0x5232
      00831F A6 08            [ 1]  702 	ld	a, #0x08
      008321 F7               [ 1]  703 	ld	(x), a
                                    704 ;	se8r01-send-hx711.c: 180: UNSET (UART1_CR2, CR2_TEN);      //  Disable transmit.
      008322 AE 52 35         [ 2]  705 	ldw	x, #0x5235
      008325 F6               [ 1]  706 	ld	a, (x)
      008326 A4 F7            [ 1]  707 	and	a, #0xf7
      008328 F7               [ 1]  708 	ld	(x), a
                                    709 ;	se8r01-send-hx711.c: 181: UNSET (UART1_CR2, CR2_REN);      //  Disable receive.
      008329 AE 52 35         [ 2]  710 	ldw	x, #0x5235
      00832C F6               [ 1]  711 	ld	a, (x)
      00832D A4 FB            [ 1]  712 	and	a, #0xfb
      00832F F7               [ 1]  713 	ld	(x), a
                                    714 ;	se8r01-send-hx711.c: 185: SET (UART1_CR3, CR3_CPOL);
      008330 AE 52 36         [ 2]  715 	ldw	x, #0x5236
      008333 F6               [ 1]  716 	ld	a, (x)
      008334 AA 04            [ 1]  717 	or	a, #0x04
      008336 F7               [ 1]  718 	ld	(x), a
                                    719 ;	se8r01-send-hx711.c: 186: SET (UART1_CR3, CR3_CPHA);
      008337 AE 52 36         [ 2]  720 	ldw	x, #0x5236
      00833A F6               [ 1]  721 	ld	a, (x)
      00833B AA 02            [ 1]  722 	or	a, #0x02
      00833D F7               [ 1]  723 	ld	(x), a
                                    724 ;	se8r01-send-hx711.c: 187: SET (UART1_CR3, CR3_LBCL);
      00833E 72 10 52 36      [ 1]  725 	bset	0x5236, #0
                                    726 ;	se8r01-send-hx711.c: 191: SET (UART1_CR2, CR2_TEN);
      008342 AE 52 35         [ 2]  727 	ldw	x, #0x5235
      008345 F6               [ 1]  728 	ld	a, (x)
      008346 AA 08            [ 1]  729 	or	a, #0x08
      008348 F7               [ 1]  730 	ld	(x), a
                                    731 ;	se8r01-send-hx711.c: 192: SET (UART1_CR2, CR2_REN);
      008349 AE 52 35         [ 2]  732 	ldw	x, #0x5235
      00834C F6               [ 1]  733 	ld	a, (x)
      00834D AA 04            [ 1]  734 	or	a, #0x04
      00834F F7               [ 1]  735 	ld	(x), a
                                    736 ;	se8r01-send-hx711.c: 193: UART1_CR3 = CR3_CLKEN;
      008350 AE 52 36         [ 2]  737 	ldw	x, #0x5236
      008353 A6 08            [ 1]  738 	ld	a, #0x08
      008355 F7               [ 1]  739 	ld	(x), a
      008356 81               [ 4]  740 	ret
                                    741 ;	se8r01-send-hx711.c: 266: void init_io(void)
                                    742 ;	-----------------------------------------
                                    743 ;	 function init_io
                                    744 ;	-----------------------------------------
      008357                        745 _init_io:
                                    746 ;	se8r01-send-hx711.c: 268: PD_DDR &= ~(1 << 3); // input mode
      008357 AE 50 11         [ 2]  747 	ldw	x, #0x5011
      00835A F6               [ 1]  748 	ld	a, (x)
      00835B A4 F7            [ 1]  749 	and	a, #0xf7
      00835D F7               [ 1]  750 	ld	(x), a
                                    751 ;	se8r01-send-hx711.c: 269: PD_CR1 |= (1 << 3); // input with pull up 
      00835E AE 50 12         [ 2]  752 	ldw	x, #0x5012
      008361 F6               [ 1]  753 	ld	a, (x)
      008362 AA 08            [ 1]  754 	or	a, #0x08
      008364 F7               [ 1]  755 	ld	(x), a
                                    756 ;	se8r01-send-hx711.c: 270: PD_CR2 |= (1 << 3); // interrupt enabled 
      008365 AE 50 13         [ 2]  757 	ldw	x, #0x5013
      008368 F6               [ 1]  758 	ld	a, (x)
      008369 AA 08            [ 1]  759 	or	a, #0x08
      00836B F7               [ 1]  760 	ld	(x), a
                                    761 ;	se8r01-send-hx711.c: 271: PD_ODR &= ~(1 << 3);
      00836C AE 50 0F         [ 2]  762 	ldw	x, #0x500f
      00836F F6               [ 1]  763 	ld	a, (x)
      008370 A4 F7            [ 1]  764 	and	a, #0xf7
      008372 F7               [ 1]  765 	ld	(x), a
                                    766 ;	se8r01-send-hx711.c: 274: PC_ODR &= ~(1 << CE);
      008373 AE 50 0A         [ 2]  767 	ldw	x, #0x500a
      008376 F6               [ 1]  768 	ld	a, (x)
      008377 A4 EF            [ 1]  769 	and	a, #0xef
      008379 F7               [ 1]  770 	ld	(x), a
                                    771 ;	se8r01-send-hx711.c: 276: PC_ODR |= (1 << CSN);
      00837A AE 50 0A         [ 2]  772 	ldw	x, #0x500a
      00837D F6               [ 1]  773 	ld	a, (x)
      00837E AA 08            [ 1]  774 	or	a, #0x08
      008380 F7               [ 1]  775 	ld	(x), a
      008381 81               [ 4]  776 	ret
                                    777 ;	se8r01-send-hx711.c: 282: void rf_switch_bank(unsigned char bankindex)
                                    778 ;	-----------------------------------------
                                    779 ;	 function rf_switch_bank
                                    780 ;	-----------------------------------------
      008382                        781 _rf_switch_bank:
      008382 88               [ 1]  782 	push	a
                                    783 ;	se8r01-send-hx711.c: 285: temp1 = bankindex;
      008383 7B 04            [ 1]  784 	ld	a, (0x04, sp)
      008385 6B 01            [ 1]  785 	ld	(0x01, sp), a
                                    786 ;	se8r01-send-hx711.c: 287: temp0 = write_spi(iRF_BANK0_STATUS);
      008387 4B 07            [ 1]  787 	push	#0x07
      008389 CD 80 A8         [ 4]  788 	call	_write_spi
      00838C 5B 01            [ 2]  789 	addw	sp, #1
                                    790 ;	se8r01-send-hx711.c: 289: if((temp0&0x80)!=temp1)
      00838E A4 80            [ 1]  791 	and	a, #0x80
      008390 11 01            [ 1]  792 	cp	a, (0x01, sp)
      008392 27 09            [ 1]  793 	jreq	00103$
                                    794 ;	se8r01-send-hx711.c: 291: write_spi_reg(iRF_CMD_ACTIVATE,0x53);
      008394 4B 53            [ 1]  795 	push	#0x53
      008396 4B 50            [ 1]  796 	push	#0x50
      008398 CD 80 CE         [ 4]  797 	call	_write_spi_reg
      00839B 5B 02            [ 2]  798 	addw	sp, #2
      00839D                        799 00103$:
      00839D 84               [ 1]  800 	pop	a
      00839E 81               [ 4]  801 	ret
                                    802 ;	se8r01-send-hx711.c: 298: void SE8R01_Calibration()
                                    803 ;	-----------------------------------------
                                    804 ;	 function SE8R01_Calibration
                                    805 ;	-----------------------------------------
      00839F                        806 _SE8R01_Calibration:
      00839F 52 0D            [ 2]  807 	sub	sp, #13
                                    808 ;	se8r01-send-hx711.c: 301: rf_switch_bank(iBANK0);
      0083A1 4B 00            [ 1]  809 	push	#0x00
      0083A3 CD 83 82         [ 4]  810 	call	_rf_switch_bank
      0083A6 84               [ 1]  811 	pop	a
                                    812 ;	se8r01-send-hx711.c: 302: temp[0]=0x03;
      0083A7 96               [ 1]  813 	ldw	x, sp
      0083A8 5C               [ 2]  814 	incw	x
      0083A9 1F 06            [ 2]  815 	ldw	(0x06, sp), x
      0083AB 1E 06            [ 2]  816 	ldw	x, (0x06, sp)
      0083AD A6 03            [ 1]  817 	ld	a, #0x03
      0083AF F7               [ 1]  818 	ld	(x), a
                                    819 ;	se8r01-send-hx711.c: 303: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_CONFIG,temp, 1);
      0083B0 1E 06            [ 2]  820 	ldw	x, (0x06, sp)
      0083B2 4B 01            [ 1]  821 	push	#0x01
      0083B4 89               [ 2]  822 	pushw	x
      0083B5 4B 20            [ 1]  823 	push	#0x20
      0083B7 CD 81 48         [ 4]  824 	call	_write_spi_buf
      0083BA 5B 04            [ 2]  825 	addw	sp, #4
                                    826 ;	se8r01-send-hx711.c: 305: temp[0]=0x32;
      0083BC 1E 06            [ 2]  827 	ldw	x, (0x06, sp)
      0083BE A6 32            [ 1]  828 	ld	a, #0x32
      0083C0 F7               [ 1]  829 	ld	(x), a
                                    830 ;	se8r01-send-hx711.c: 307: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_RF_CH, temp,1);
      0083C1 1E 06            [ 2]  831 	ldw	x, (0x06, sp)
      0083C3 4B 01            [ 1]  832 	push	#0x01
      0083C5 89               [ 2]  833 	pushw	x
      0083C6 4B 25            [ 1]  834 	push	#0x25
      0083C8 CD 81 48         [ 4]  835 	call	_write_spi_buf
      0083CB 5B 04            [ 2]  836 	addw	sp, #4
                                    837 ;	se8r01-send-hx711.c: 311: if (SE8R01_DR_2M==1)
      0083CD CE 00 10         [ 2]  838 	ldw	x, _SE8R01_DR_2M+0
      0083D0 A3 00 01         [ 2]  839 	cpw	x, #0x0001
      0083D3 26 07            [ 1]  840 	jrne	00105$
                                    841 ;	se8r01-send-hx711.c: 312: {temp[0]=0x48;}
      0083D5 1E 06            [ 2]  842 	ldw	x, (0x06, sp)
      0083D7 A6 48            [ 1]  843 	ld	a, #0x48
      0083D9 F7               [ 1]  844 	ld	(x), a
      0083DA 20 14            [ 2]  845 	jra	00106$
      0083DC                        846 00105$:
                                    847 ;	se8r01-send-hx711.c: 313: else if (SE8R01_DR_1M==1)
      0083DC CE 00 12         [ 2]  848 	ldw	x, _SE8R01_DR_1M+0
      0083DF A3 00 01         [ 2]  849 	cpw	x, #0x0001
      0083E2 26 07            [ 1]  850 	jrne	00102$
                                    851 ;	se8r01-send-hx711.c: 314: {temp[0]=0x40;}
      0083E4 1E 06            [ 2]  852 	ldw	x, (0x06, sp)
      0083E6 A6 40            [ 1]  853 	ld	a, #0x40
      0083E8 F7               [ 1]  854 	ld	(x), a
      0083E9 20 05            [ 2]  855 	jra	00106$
      0083EB                        856 00102$:
                                    857 ;	se8r01-send-hx711.c: 316: {temp[0]=0x68;}   
      0083EB 1E 06            [ 2]  858 	ldw	x, (0x06, sp)
      0083ED A6 68            [ 1]  859 	ld	a, #0x68
      0083EF F7               [ 1]  860 	ld	(x), a
      0083F0                        861 00106$:
                                    862 ;	se8r01-send-hx711.c: 318: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_RF_SETUP,temp,1);
      0083F0 1E 06            [ 2]  863 	ldw	x, (0x06, sp)
      0083F2 4B 01            [ 1]  864 	push	#0x01
      0083F4 89               [ 2]  865 	pushw	x
      0083F5 4B 26            [ 1]  866 	push	#0x26
      0083F7 CD 81 48         [ 4]  867 	call	_write_spi_buf
      0083FA 5B 04            [ 2]  868 	addw	sp, #4
                                    869 ;	se8r01-send-hx711.c: 319: temp[0]=0x77;
      0083FC 1E 06            [ 2]  870 	ldw	x, (0x06, sp)
      0083FE A6 77            [ 1]  871 	ld	a, #0x77
      008400 F7               [ 1]  872 	ld	(x), a
                                    873 ;	se8r01-send-hx711.c: 320: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_PRE_GURD, temp,1);
      008401 1E 06            [ 2]  874 	ldw	x, (0x06, sp)
      008403 4B 01            [ 1]  875 	push	#0x01
      008405 89               [ 2]  876 	pushw	x
      008406 4B 3F            [ 1]  877 	push	#0x3f
      008408 CD 81 48         [ 4]  878 	call	_write_spi_buf
      00840B 5B 04            [ 2]  879 	addw	sp, #4
                                    880 ;	se8r01-send-hx711.c: 322: rf_switch_bank(iBANK1);
      00840D 4B 80            [ 1]  881 	push	#0x80
      00840F CD 83 82         [ 4]  882 	call	_rf_switch_bank
      008412 84               [ 1]  883 	pop	a
                                    884 ;	se8r01-send-hx711.c: 323: temp[0]=0x40;
      008413 1E 06            [ 2]  885 	ldw	x, (0x06, sp)
      008415 A6 40            [ 1]  886 	ld	a, #0x40
      008417 F7               [ 1]  887 	ld	(x), a
                                    888 ;	se8r01-send-hx711.c: 324: temp[1]=0x00;
      008418 1E 06            [ 2]  889 	ldw	x, (0x06, sp)
      00841A 5C               [ 2]  890 	incw	x
      00841B 1F 0C            [ 2]  891 	ldw	(0x0c, sp), x
      00841D 1E 0C            [ 2]  892 	ldw	x, (0x0c, sp)
      00841F 7F               [ 1]  893 	clr	(x)
                                    894 ;	se8r01-send-hx711.c: 325: temp[2]=0x10;
      008420 1E 06            [ 2]  895 	ldw	x, (0x06, sp)
      008422 5C               [ 2]  896 	incw	x
      008423 5C               [ 2]  897 	incw	x
      008424 1F 0A            [ 2]  898 	ldw	(0x0a, sp), x
      008426 1E 0A            [ 2]  899 	ldw	x, (0x0a, sp)
      008428 A6 10            [ 1]  900 	ld	a, #0x10
      00842A F7               [ 1]  901 	ld	(x), a
                                    902 ;	se8r01-send-hx711.c: 327: {temp[3]=0xE6;}
      00842B 1E 06            [ 2]  903 	ldw	x, (0x06, sp)
      00842D 1C 00 03         [ 2]  904 	addw	x, #0x0003
      008430 1F 08            [ 2]  905 	ldw	(0x08, sp), x
                                    906 ;	se8r01-send-hx711.c: 326: if (SE8R01_DR_2M==1)
      008432 CE 00 10         [ 2]  907 	ldw	x, _SE8R01_DR_2M+0
      008435 A3 00 01         [ 2]  908 	cpw	x, #0x0001
      008438 26 07            [ 1]  909 	jrne	00108$
                                    910 ;	se8r01-send-hx711.c: 327: {temp[3]=0xE6;}
      00843A 1E 08            [ 2]  911 	ldw	x, (0x08, sp)
      00843C A6 E6            [ 1]  912 	ld	a, #0xe6
      00843E F7               [ 1]  913 	ld	(x), a
      00843F 20 05            [ 2]  914 	jra	00109$
      008441                        915 00108$:
                                    916 ;	se8r01-send-hx711.c: 329: {temp[3]=0xE4;}
      008441 1E 08            [ 2]  917 	ldw	x, (0x08, sp)
      008443 A6 E4            [ 1]  918 	ld	a, #0xe4
      008445 F7               [ 1]  919 	ld	(x), a
      008446                        920 00109$:
                                    921 ;	se8r01-send-hx711.c: 331: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_PLL_CTL0, temp, 4);
      008446 1E 06            [ 2]  922 	ldw	x, (0x06, sp)
      008448 4B 04            [ 1]  923 	push	#0x04
      00844A 89               [ 2]  924 	pushw	x
      00844B 4B 21            [ 1]  925 	push	#0x21
      00844D CD 81 48         [ 4]  926 	call	_write_spi_buf
      008450 5B 04            [ 2]  927 	addw	sp, #4
                                    928 ;	se8r01-send-hx711.c: 333: temp[0]=0x20;
      008452 1E 06            [ 2]  929 	ldw	x, (0x06, sp)
      008454 A6 20            [ 1]  930 	ld	a, #0x20
      008456 F7               [ 1]  931 	ld	(x), a
                                    932 ;	se8r01-send-hx711.c: 334: temp[1]=0x08;
      008457 1E 0C            [ 2]  933 	ldw	x, (0x0c, sp)
      008459 A6 08            [ 1]  934 	ld	a, #0x08
      00845B F7               [ 1]  935 	ld	(x), a
                                    936 ;	se8r01-send-hx711.c: 335: temp[2]=0x50;
      00845C 1E 0A            [ 2]  937 	ldw	x, (0x0a, sp)
      00845E A6 50            [ 1]  938 	ld	a, #0x50
      008460 F7               [ 1]  939 	ld	(x), a
                                    940 ;	se8r01-send-hx711.c: 336: temp[3]=0x40;
      008461 1E 08            [ 2]  941 	ldw	x, (0x08, sp)
      008463 A6 40            [ 1]  942 	ld	a, #0x40
      008465 F7               [ 1]  943 	ld	(x), a
                                    944 ;	se8r01-send-hx711.c: 337: temp[4]=0x50;
      008466 1E 06            [ 2]  945 	ldw	x, (0x06, sp)
      008468 A6 50            [ 1]  946 	ld	a, #0x50
      00846A E7 04            [ 1]  947 	ld	(0x0004, x), a
                                    948 ;	se8r01-send-hx711.c: 338: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_CAL_CTL, temp, 5);
      00846C 1E 06            [ 2]  949 	ldw	x, (0x06, sp)
      00846E 4B 05            [ 1]  950 	push	#0x05
      008470 89               [ 2]  951 	pushw	x
      008471 4B 23            [ 1]  952 	push	#0x23
      008473 CD 81 48         [ 4]  953 	call	_write_spi_buf
      008476 5B 04            [ 2]  954 	addw	sp, #4
                                    955 ;	se8r01-send-hx711.c: 340: temp[0]=0x00;
      008478 1E 06            [ 2]  956 	ldw	x, (0x06, sp)
      00847A 7F               [ 1]  957 	clr	(x)
                                    958 ;	se8r01-send-hx711.c: 341: temp[1]=0x00;
      00847B 1E 0C            [ 2]  959 	ldw	x, (0x0c, sp)
      00847D 7F               [ 1]  960 	clr	(x)
                                    961 ;	se8r01-send-hx711.c: 342: if (SE8R01_DR_2M==1)
      00847E CE 00 10         [ 2]  962 	ldw	x, _SE8R01_DR_2M+0
      008481 A3 00 01         [ 2]  963 	cpw	x, #0x0001
      008484 26 07            [ 1]  964 	jrne	00111$
                                    965 ;	se8r01-send-hx711.c: 343: { temp[2]=0x1E;}
      008486 1E 0A            [ 2]  966 	ldw	x, (0x0a, sp)
      008488 A6 1E            [ 1]  967 	ld	a, #0x1e
      00848A F7               [ 1]  968 	ld	(x), a
      00848B 20 05            [ 2]  969 	jra	00112$
      00848D                        970 00111$:
                                    971 ;	se8r01-send-hx711.c: 345: { temp[2]=0x1F;}
      00848D 1E 0A            [ 2]  972 	ldw	x, (0x0a, sp)
      00848F A6 1F            [ 1]  973 	ld	a, #0x1f
      008491 F7               [ 1]  974 	ld	(x), a
      008492                        975 00112$:
                                    976 ;	se8r01-send-hx711.c: 347: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_IF_FREQ, temp, 3);
      008492 1E 06            [ 2]  977 	ldw	x, (0x06, sp)
      008494 4B 03            [ 1]  978 	push	#0x03
      008496 89               [ 2]  979 	pushw	x
      008497 4B 2A            [ 1]  980 	push	#0x2a
      008499 CD 81 48         [ 4]  981 	call	_write_spi_buf
      00849C 5B 04            [ 2]  982 	addw	sp, #4
                                    983 ;	se8r01-send-hx711.c: 349: if (SE8R01_DR_2M==1)
      00849E CE 00 10         [ 2]  984 	ldw	x, _SE8R01_DR_2M+0
      0084A1 A3 00 01         [ 2]  985 	cpw	x, #0x0001
      0084A4 26 07            [ 1]  986 	jrne	00114$
                                    987 ;	se8r01-send-hx711.c: 350: { temp[0]=0x29;}
      0084A6 1E 06            [ 2]  988 	ldw	x, (0x06, sp)
      0084A8 A6 29            [ 1]  989 	ld	a, #0x29
      0084AA F7               [ 1]  990 	ld	(x), a
      0084AB 20 05            [ 2]  991 	jra	00115$
      0084AD                        992 00114$:
                                    993 ;	se8r01-send-hx711.c: 352: { temp[0]=0x14;}
      0084AD 1E 06            [ 2]  994 	ldw	x, (0x06, sp)
      0084AF A6 14            [ 1]  995 	ld	a, #0x14
      0084B1 F7               [ 1]  996 	ld	(x), a
      0084B2                        997 00115$:
                                    998 ;	se8r01-send-hx711.c: 354: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_FDEV, temp, 1);
      0084B2 1E 06            [ 2]  999 	ldw	x, (0x06, sp)
      0084B4 4B 01            [ 1] 1000 	push	#0x01
      0084B6 89               [ 2] 1001 	pushw	x
      0084B7 4B 2C            [ 1] 1002 	push	#0x2c
      0084B9 CD 81 48         [ 4] 1003 	call	_write_spi_buf
      0084BC 5B 04            [ 2] 1004 	addw	sp, #4
                                   1005 ;	se8r01-send-hx711.c: 356: temp[0]=0x00;
      0084BE 1E 06            [ 2] 1006 	ldw	x, (0x06, sp)
      0084C0 7F               [ 1] 1007 	clr	(x)
                                   1008 ;	se8r01-send-hx711.c: 357: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_DAC_CAL_LOW,temp,1);
      0084C1 1E 06            [ 2] 1009 	ldw	x, (0x06, sp)
      0084C3 4B 01            [ 1] 1010 	push	#0x01
      0084C5 89               [ 2] 1011 	pushw	x
      0084C6 4B 37            [ 1] 1012 	push	#0x37
      0084C8 CD 81 48         [ 4] 1013 	call	_write_spi_buf
      0084CB 5B 04            [ 2] 1014 	addw	sp, #4
                                   1015 ;	se8r01-send-hx711.c: 359: temp[0]=0x7F;
      0084CD 1E 06            [ 2] 1016 	ldw	x, (0x06, sp)
      0084CF A6 7F            [ 1] 1017 	ld	a, #0x7f
      0084D1 F7               [ 1] 1018 	ld	(x), a
                                   1019 ;	se8r01-send-hx711.c: 360: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_DAC_CAL_HI,temp,1);
      0084D2 1E 06            [ 2] 1020 	ldw	x, (0x06, sp)
      0084D4 4B 01            [ 1] 1021 	push	#0x01
      0084D6 89               [ 2] 1022 	pushw	x
      0084D7 4B 38            [ 1] 1023 	push	#0x38
      0084D9 CD 81 48         [ 4] 1024 	call	_write_spi_buf
      0084DC 5B 04            [ 2] 1025 	addw	sp, #4
                                   1026 ;	se8r01-send-hx711.c: 362: temp[0]=0x02;
      0084DE 1E 06            [ 2] 1027 	ldw	x, (0x06, sp)
      0084E0 A6 02            [ 1] 1028 	ld	a, #0x02
      0084E2 F7               [ 1] 1029 	ld	(x), a
                                   1030 ;	se8r01-send-hx711.c: 363: temp[1]=0xC1;
      0084E3 1E 0C            [ 2] 1031 	ldw	x, (0x0c, sp)
      0084E5 A6 C1            [ 1] 1032 	ld	a, #0xc1
      0084E7 F7               [ 1] 1033 	ld	(x), a
                                   1034 ;	se8r01-send-hx711.c: 364: temp[2]=0xEB;            
      0084E8 1E 0A            [ 2] 1035 	ldw	x, (0x0a, sp)
      0084EA A6 EB            [ 1] 1036 	ld	a, #0xeb
      0084EC F7               [ 1] 1037 	ld	(x), a
                                   1038 ;	se8r01-send-hx711.c: 365: temp[3]=0x1C;
      0084ED 1E 08            [ 2] 1039 	ldw	x, (0x08, sp)
      0084EF A6 1C            [ 1] 1040 	ld	a, #0x1c
      0084F1 F7               [ 1] 1041 	ld	(x), a
                                   1042 ;	se8r01-send-hx711.c: 366: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_AGC_GAIN, temp,4);
      0084F2 1E 06            [ 2] 1043 	ldw	x, (0x06, sp)
      0084F4 4B 04            [ 1] 1044 	push	#0x04
      0084F6 89               [ 2] 1045 	pushw	x
      0084F7 4B 3D            [ 1] 1046 	push	#0x3d
      0084F9 CD 81 48         [ 4] 1047 	call	_write_spi_buf
      0084FC 5B 04            [ 2] 1048 	addw	sp, #4
                                   1049 ;	se8r01-send-hx711.c: 368: temp[0]=0x97;
      0084FE 1E 06            [ 2] 1050 	ldw	x, (0x06, sp)
      008500 A6 97            [ 1] 1051 	ld	a, #0x97
      008502 F7               [ 1] 1052 	ld	(x), a
                                   1053 ;	se8r01-send-hx711.c: 369: temp[1]=0x64;
      008503 1E 0C            [ 2] 1054 	ldw	x, (0x0c, sp)
      008505 A6 64            [ 1] 1055 	ld	a, #0x64
      008507 F7               [ 1] 1056 	ld	(x), a
                                   1057 ;	se8r01-send-hx711.c: 370: temp[2]=0x00;
      008508 1E 0A            [ 2] 1058 	ldw	x, (0x0a, sp)
      00850A 7F               [ 1] 1059 	clr	(x)
                                   1060 ;	se8r01-send-hx711.c: 371: temp[3]=0x81;
      00850B 1E 08            [ 2] 1061 	ldw	x, (0x08, sp)
      00850D A6 81            [ 1] 1062 	ld	a, #0x81
      00850F F7               [ 1] 1063 	ld	(x), a
                                   1064 ;	se8r01-send-hx711.c: 372: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_RF_IVGEN, temp, 4);
      008510 1E 06            [ 2] 1065 	ldw	x, (0x06, sp)
      008512 4B 04            [ 1] 1066 	push	#0x04
      008514 89               [ 2] 1067 	pushw	x
      008515 4B 3E            [ 1] 1068 	push	#0x3e
      008517 CD 81 48         [ 4] 1069 	call	_write_spi_buf
      00851A 5B 04            [ 2] 1070 	addw	sp, #4
                                   1071 ;	se8r01-send-hx711.c: 373: rf_switch_bank(iBANK0);
      00851C 4B 00            [ 1] 1072 	push	#0x00
      00851E CD 83 82         [ 4] 1073 	call	_rf_switch_bank
      008521 84               [ 1] 1074 	pop	a
                                   1075 ;	se8r01-send-hx711.c: 378: delayTenMicro();
      008522 CD 80 A0         [ 4] 1076 	call	_delayTenMicro
                                   1077 ;	se8r01-send-hx711.c: 379: PC_ODR |= (1 << CE);
      008525 AE 50 0A         [ 2] 1078 	ldw	x, #0x500a
      008528 F6               [ 1] 1079 	ld	a, (x)
      008529 AA 10            [ 1] 1080 	or	a, #0x10
      00852B F7               [ 1] 1081 	ld	(x), a
                                   1082 ;	se8r01-send-hx711.c: 380: delayTenMicro();
      00852C CD 80 A0         [ 4] 1083 	call	_delayTenMicro
                                   1084 ;	se8r01-send-hx711.c: 381: delayTenMicro();
      00852F CD 80 A0         [ 4] 1085 	call	_delayTenMicro
                                   1086 ;	se8r01-send-hx711.c: 382: delayTenMicro();
      008532 CD 80 A0         [ 4] 1087 	call	_delayTenMicro
                                   1088 ;	se8r01-send-hx711.c: 383: PC_ODR &= ~(1 << CE);
      008535 AE 50 0A         [ 2] 1089 	ldw	x, #0x500a
      008538 F6               [ 1] 1090 	ld	a, (x)
      008539 A4 EF            [ 1] 1091 	and	a, #0xef
      00853B F7               [ 1] 1092 	ld	(x), a
                                   1093 ;	se8r01-send-hx711.c: 384: delay(50);                            // delay 50ms waitting for calibaration.
      00853C 4B 32            [ 1] 1094 	push	#0x32
      00853E 4B 00            [ 1] 1095 	push	#0x00
      008540 CD 82 2E         [ 4] 1096 	call	_delay
      008543 5B 02            [ 2] 1097 	addw	sp, #2
                                   1098 ;	se8r01-send-hx711.c: 389: delayTenMicro();
      008545 CD 80 A0         [ 4] 1099 	call	_delayTenMicro
                                   1100 ;	se8r01-send-hx711.c: 390: PC_ODR |= (1 << CE);
      008548 AE 50 0A         [ 2] 1101 	ldw	x, #0x500a
      00854B F6               [ 1] 1102 	ld	a, (x)
      00854C AA 10            [ 1] 1103 	or	a, #0x10
      00854E F7               [ 1] 1104 	ld	(x), a
                                   1105 ;	se8r01-send-hx711.c: 391: delayTenMicro();
      00854F CD 80 A0         [ 4] 1106 	call	_delayTenMicro
                                   1107 ;	se8r01-send-hx711.c: 392: delayTenMicro();
      008552 CD 80 A0         [ 4] 1108 	call	_delayTenMicro
                                   1109 ;	se8r01-send-hx711.c: 393: delayTenMicro();
      008555 CD 80 A0         [ 4] 1110 	call	_delayTenMicro
                                   1111 ;	se8r01-send-hx711.c: 394: PC_ODR &= ~(1 << CE);
      008558 AE 50 0A         [ 2] 1112 	ldw	x, #0x500a
      00855B F6               [ 1] 1113 	ld	a, (x)
      00855C A4 EF            [ 1] 1114 	and	a, #0xef
      00855E F7               [ 1] 1115 	ld	(x), a
                                   1116 ;	se8r01-send-hx711.c: 395: delay(50);                            // delay 50ms waitting for calibaration.
      00855F 4B 32            [ 1] 1117 	push	#0x32
      008561 4B 00            [ 1] 1118 	push	#0x00
      008563 CD 82 2E         [ 4] 1119 	call	_delay
      008566 5B 02            [ 2] 1120 	addw	sp, #2
      008568 5B 0D            [ 2] 1121 	addw	sp, #13
      00856A 81               [ 4] 1122 	ret
                                   1123 ;	se8r01-send-hx711.c: 399: void SE8R01_Analog_Init()           //SE8R01 初始化
                                   1124 ;	-----------------------------------------
                                   1125 ;	 function SE8R01_Analog_Init
                                   1126 ;	-----------------------------------------
      00856B                       1127 _SE8R01_Analog_Init:
      00856B 52 15            [ 2] 1128 	sub	sp, #21
                                   1129 ;	se8r01-send-hx711.c: 404: gtemp[0]=0x28;
      00856D AE 00 01         [ 2] 1130 	ldw	x, #_gtemp+0
      008570 1F 14            [ 2] 1131 	ldw	(0x14, sp), x
      008572 1E 14            [ 2] 1132 	ldw	x, (0x14, sp)
      008574 A6 28            [ 1] 1133 	ld	a, #0x28
      008576 F7               [ 1] 1134 	ld	(x), a
                                   1135 ;	se8r01-send-hx711.c: 405: gtemp[1]=0x32;
      008577 1E 14            [ 2] 1136 	ldw	x, (0x14, sp)
      008579 5C               [ 2] 1137 	incw	x
      00857A 1F 12            [ 2] 1138 	ldw	(0x12, sp), x
      00857C 1E 12            [ 2] 1139 	ldw	x, (0x12, sp)
      00857E A6 32            [ 1] 1140 	ld	a, #0x32
      008580 F7               [ 1] 1141 	ld	(x), a
                                   1142 ;	se8r01-send-hx711.c: 406: gtemp[2]=0x80;
      008581 1E 14            [ 2] 1143 	ldw	x, (0x14, sp)
      008583 5C               [ 2] 1144 	incw	x
      008584 5C               [ 2] 1145 	incw	x
      008585 1F 10            [ 2] 1146 	ldw	(0x10, sp), x
      008587 1E 10            [ 2] 1147 	ldw	x, (0x10, sp)
      008589 A6 80            [ 1] 1148 	ld	a, #0x80
      00858B F7               [ 1] 1149 	ld	(x), a
                                   1150 ;	se8r01-send-hx711.c: 407: gtemp[3]=0x90;
      00858C 1E 14            [ 2] 1151 	ldw	x, (0x14, sp)
      00858E 1C 00 03         [ 2] 1152 	addw	x, #0x0003
      008591 1F 0E            [ 2] 1153 	ldw	(0x0e, sp), x
      008593 1E 0E            [ 2] 1154 	ldw	x, (0x0e, sp)
      008595 A6 90            [ 1] 1155 	ld	a, #0x90
      008597 F7               [ 1] 1156 	ld	(x), a
                                   1157 ;	se8r01-send-hx711.c: 408: gtemp[4]=0x00;
      008598 1E 14            [ 2] 1158 	ldw	x, (0x14, sp)
      00859A 1C 00 04         [ 2] 1159 	addw	x, #0x0004
      00859D 7F               [ 1] 1160 	clr	(x)
                                   1161 ;	se8r01-send-hx711.c: 409: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_SETUP_VALUE, gtemp, 5);
      00859E 1E 14            [ 2] 1162 	ldw	x, (0x14, sp)
      0085A0 4B 05            [ 1] 1163 	push	#0x05
      0085A2 89               [ 2] 1164 	pushw	x
      0085A3 4B 3E            [ 1] 1165 	push	#0x3e
      0085A5 CD 81 48         [ 4] 1166 	call	_write_spi_buf
      0085A8 5B 04            [ 2] 1167 	addw	sp, #4
                                   1168 ;	se8r01-send-hx711.c: 410: delay(2);
      0085AA 4B 02            [ 1] 1169 	push	#0x02
      0085AC 4B 00            [ 1] 1170 	push	#0x00
      0085AE CD 82 2E         [ 4] 1171 	call	_delay
      0085B1 5B 02            [ 2] 1172 	addw	sp, #2
                                   1173 ;	se8r01-send-hx711.c: 413: rf_switch_bank(iBANK1);
      0085B3 4B 80            [ 1] 1174 	push	#0x80
      0085B5 CD 83 82         [ 4] 1175 	call	_rf_switch_bank
      0085B8 84               [ 1] 1176 	pop	a
                                   1177 ;	se8r01-send-hx711.c: 415: temp[0]=0x40;
      0085B9 96               [ 1] 1178 	ldw	x, sp
      0085BA 5C               [ 2] 1179 	incw	x
      0085BB 1F 0C            [ 2] 1180 	ldw	(0x0c, sp), x
      0085BD 1E 0C            [ 2] 1181 	ldw	x, (0x0c, sp)
      0085BF A6 40            [ 1] 1182 	ld	a, #0x40
      0085C1 F7               [ 1] 1183 	ld	(x), a
                                   1184 ;	se8r01-send-hx711.c: 416: temp[1]=0x01;               
      0085C2 1E 0C            [ 2] 1185 	ldw	x, (0x0c, sp)
      0085C4 5C               [ 2] 1186 	incw	x
      0085C5 1F 0A            [ 2] 1187 	ldw	(0x0a, sp), x
      0085C7 1E 0A            [ 2] 1188 	ldw	x, (0x0a, sp)
      0085C9 A6 01            [ 1] 1189 	ld	a, #0x01
      0085CB F7               [ 1] 1190 	ld	(x), a
                                   1191 ;	se8r01-send-hx711.c: 417: temp[2]=0x30;               
      0085CC 1E 0C            [ 2] 1192 	ldw	x, (0x0c, sp)
      0085CE 5C               [ 2] 1193 	incw	x
      0085CF 5C               [ 2] 1194 	incw	x
      0085D0 1F 08            [ 2] 1195 	ldw	(0x08, sp), x
      0085D2 1E 08            [ 2] 1196 	ldw	x, (0x08, sp)
      0085D4 A6 30            [ 1] 1197 	ld	a, #0x30
      0085D6 F7               [ 1] 1198 	ld	(x), a
                                   1199 ;	se8r01-send-hx711.c: 419: { temp[3]=0xE2; }              
      0085D7 1E 0C            [ 2] 1200 	ldw	x, (0x0c, sp)
      0085D9 1C 00 03         [ 2] 1201 	addw	x, #0x0003
      0085DC 1F 06            [ 2] 1202 	ldw	(0x06, sp), x
                                   1203 ;	se8r01-send-hx711.c: 418: if (SE8R01_DR_2M==1)
      0085DE CE 00 10         [ 2] 1204 	ldw	x, _SE8R01_DR_2M+0
      0085E1 A3 00 01         [ 2] 1205 	cpw	x, #0x0001
      0085E4 26 07            [ 1] 1206 	jrne	00102$
                                   1207 ;	se8r01-send-hx711.c: 419: { temp[3]=0xE2; }              
      0085E6 1E 06            [ 2] 1208 	ldw	x, (0x06, sp)
      0085E8 A6 E2            [ 1] 1209 	ld	a, #0xe2
      0085EA F7               [ 1] 1210 	ld	(x), a
      0085EB 20 05            [ 2] 1211 	jra	00103$
      0085ED                       1212 00102$:
                                   1213 ;	se8r01-send-hx711.c: 421: { temp[3]=0xE0;}
      0085ED 1E 06            [ 2] 1214 	ldw	x, (0x06, sp)
      0085EF A6 E0            [ 1] 1215 	ld	a, #0xe0
      0085F1 F7               [ 1] 1216 	ld	(x), a
      0085F2                       1217 00103$:
                                   1218 ;	se8r01-send-hx711.c: 423: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_PLL_CTL0, temp,4);
      0085F2 1E 0C            [ 2] 1219 	ldw	x, (0x0c, sp)
      0085F4 4B 04            [ 1] 1220 	push	#0x04
      0085F6 89               [ 2] 1221 	pushw	x
      0085F7 4B 21            [ 1] 1222 	push	#0x21
      0085F9 CD 81 48         [ 4] 1223 	call	_write_spi_buf
      0085FC 5B 04            [ 2] 1224 	addw	sp, #4
                                   1225 ;	se8r01-send-hx711.c: 425: temp[0]=0x29;
      0085FE 1E 0C            [ 2] 1226 	ldw	x, (0x0c, sp)
      008600 A6 29            [ 1] 1227 	ld	a, #0x29
      008602 F7               [ 1] 1228 	ld	(x), a
                                   1229 ;	se8r01-send-hx711.c: 426: temp[1]=0x89;
      008603 1E 0A            [ 2] 1230 	ldw	x, (0x0a, sp)
      008605 A6 89            [ 1] 1231 	ld	a, #0x89
      008607 F7               [ 1] 1232 	ld	(x), a
                                   1233 ;	se8r01-send-hx711.c: 427: temp[2]=0x55;                     
      008608 1E 08            [ 2] 1234 	ldw	x, (0x08, sp)
      00860A A6 55            [ 1] 1235 	ld	a, #0x55
      00860C F7               [ 1] 1236 	ld	(x), a
                                   1237 ;	se8r01-send-hx711.c: 428: temp[3]=0x40;
      00860D 1E 06            [ 2] 1238 	ldw	x, (0x06, sp)
      00860F A6 40            [ 1] 1239 	ld	a, #0x40
      008611 F7               [ 1] 1240 	ld	(x), a
                                   1241 ;	se8r01-send-hx711.c: 429: temp[4]=0x50;
      008612 1E 0C            [ 2] 1242 	ldw	x, (0x0c, sp)
      008614 A6 50            [ 1] 1243 	ld	a, #0x50
      008616 E7 04            [ 1] 1244 	ld	(0x0004, x), a
                                   1245 ;	se8r01-send-hx711.c: 430: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_CAL_CTL, temp,5);
      008618 1E 0C            [ 2] 1246 	ldw	x, (0x0c, sp)
      00861A 4B 05            [ 1] 1247 	push	#0x05
      00861C 89               [ 2] 1248 	pushw	x
      00861D 4B 23            [ 1] 1249 	push	#0x23
      00861F CD 81 48         [ 4] 1250 	call	_write_spi_buf
      008622 5B 04            [ 2] 1251 	addw	sp, #4
                                   1252 ;	se8r01-send-hx711.c: 432: if (SE8R01_DR_2M==1)
      008624 CE 00 10         [ 2] 1253 	ldw	x, _SE8R01_DR_2M+0
      008627 A3 00 01         [ 2] 1254 	cpw	x, #0x0001
      00862A 26 07            [ 1] 1255 	jrne	00105$
                                   1256 ;	se8r01-send-hx711.c: 433: { temp[0]=0x29;}
      00862C 1E 0C            [ 2] 1257 	ldw	x, (0x0c, sp)
      00862E A6 29            [ 1] 1258 	ld	a, #0x29
      008630 F7               [ 1] 1259 	ld	(x), a
      008631 20 05            [ 2] 1260 	jra	00106$
      008633                       1261 00105$:
                                   1262 ;	se8r01-send-hx711.c: 435: { temp[0]=0x14;}
      008633 1E 0C            [ 2] 1263 	ldw	x, (0x0c, sp)
      008635 A6 14            [ 1] 1264 	ld	a, #0x14
      008637 F7               [ 1] 1265 	ld	(x), a
      008638                       1266 00106$:
                                   1267 ;	se8r01-send-hx711.c: 437: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_FDEV, temp,1);
      008638 1E 0C            [ 2] 1268 	ldw	x, (0x0c, sp)
      00863A 4B 01            [ 1] 1269 	push	#0x01
      00863C 89               [ 2] 1270 	pushw	x
      00863D 4B 2C            [ 1] 1271 	push	#0x2c
      00863F CD 81 48         [ 4] 1272 	call	_write_spi_buf
      008642 5B 04            [ 2] 1273 	addw	sp, #4
                                   1274 ;	se8r01-send-hx711.c: 439: temp[0]=0x55;
      008644 1E 0C            [ 2] 1275 	ldw	x, (0x0c, sp)
      008646 A6 55            [ 1] 1276 	ld	a, #0x55
      008648 F7               [ 1] 1277 	ld	(x), a
                                   1278 ;	se8r01-send-hx711.c: 440: temp[1]=0xC2;
      008649 1E 0A            [ 2] 1279 	ldw	x, (0x0a, sp)
      00864B A6 C2            [ 1] 1280 	ld	a, #0xc2
      00864D F7               [ 1] 1281 	ld	(x), a
                                   1282 ;	se8r01-send-hx711.c: 441: temp[2]=0x09;
      00864E 1E 08            [ 2] 1283 	ldw	x, (0x08, sp)
      008650 A6 09            [ 1] 1284 	ld	a, #0x09
      008652 F7               [ 1] 1285 	ld	(x), a
                                   1286 ;	se8r01-send-hx711.c: 442: temp[3]=0xAC;  
      008653 1E 06            [ 2] 1287 	ldw	x, (0x06, sp)
      008655 A6 AC            [ 1] 1288 	ld	a, #0xac
      008657 F7               [ 1] 1289 	ld	(x), a
                                   1290 ;	se8r01-send-hx711.c: 443: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_RX_CTRL,temp,4);
      008658 1E 0C            [ 2] 1291 	ldw	x, (0x0c, sp)
      00865A 4B 04            [ 1] 1292 	push	#0x04
      00865C 89               [ 2] 1293 	pushw	x
      00865D 4B 31            [ 1] 1294 	push	#0x31
      00865F CD 81 48         [ 4] 1295 	call	_write_spi_buf
      008662 5B 04            [ 2] 1296 	addw	sp, #4
                                   1297 ;	se8r01-send-hx711.c: 445: temp[0]=0x00;
      008664 1E 0C            [ 2] 1298 	ldw	x, (0x0c, sp)
      008666 7F               [ 1] 1299 	clr	(x)
                                   1300 ;	se8r01-send-hx711.c: 446: temp[1]=0x14;
      008667 1E 0A            [ 2] 1301 	ldw	x, (0x0a, sp)
      008669 A6 14            [ 1] 1302 	ld	a, #0x14
      00866B F7               [ 1] 1303 	ld	(x), a
                                   1304 ;	se8r01-send-hx711.c: 447: temp[2]=0x08;   
      00866C 1E 08            [ 2] 1305 	ldw	x, (0x08, sp)
      00866E A6 08            [ 1] 1306 	ld	a, #0x08
      008670 F7               [ 1] 1307 	ld	(x), a
                                   1308 ;	se8r01-send-hx711.c: 448: temp[3]=0x29;
      008671 1E 06            [ 2] 1309 	ldw	x, (0x06, sp)
      008673 A6 29            [ 1] 1310 	ld	a, #0x29
      008675 F7               [ 1] 1311 	ld	(x), a
                                   1312 ;	se8r01-send-hx711.c: 449: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_FAGC_CTRL_1, temp,4);
      008676 1E 0C            [ 2] 1313 	ldw	x, (0x0c, sp)
      008678 4B 04            [ 1] 1314 	push	#0x04
      00867A 89               [ 2] 1315 	pushw	x
      00867B 4B 33            [ 1] 1316 	push	#0x33
      00867D CD 81 48         [ 4] 1317 	call	_write_spi_buf
      008680 5B 04            [ 2] 1318 	addw	sp, #4
                                   1319 ;	se8r01-send-hx711.c: 451: temp[0]=0x02;
      008682 1E 0C            [ 2] 1320 	ldw	x, (0x0c, sp)
      008684 A6 02            [ 1] 1321 	ld	a, #0x02
      008686 F7               [ 1] 1322 	ld	(x), a
                                   1323 ;	se8r01-send-hx711.c: 452: temp[1]=0xC1;
      008687 1E 0A            [ 2] 1324 	ldw	x, (0x0a, sp)
      008689 A6 C1            [ 1] 1325 	ld	a, #0xc1
      00868B F7               [ 1] 1326 	ld	(x), a
                                   1327 ;	se8r01-send-hx711.c: 453: temp[2]=0xCB;  
      00868C 1E 08            [ 2] 1328 	ldw	x, (0x08, sp)
      00868E A6 CB            [ 1] 1329 	ld	a, #0xcb
      008690 F7               [ 1] 1330 	ld	(x), a
                                   1331 ;	se8r01-send-hx711.c: 454: temp[3]=0x1C;
      008691 1E 06            [ 2] 1332 	ldw	x, (0x06, sp)
      008693 A6 1C            [ 1] 1333 	ld	a, #0x1c
      008695 F7               [ 1] 1334 	ld	(x), a
                                   1335 ;	se8r01-send-hx711.c: 455: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_AGC_GAIN, temp,4);
      008696 1E 0C            [ 2] 1336 	ldw	x, (0x0c, sp)
      008698 4B 04            [ 1] 1337 	push	#0x04
      00869A 89               [ 2] 1338 	pushw	x
      00869B 4B 3D            [ 1] 1339 	push	#0x3d
      00869D CD 81 48         [ 4] 1340 	call	_write_spi_buf
      0086A0 5B 04            [ 2] 1341 	addw	sp, #4
                                   1342 ;	se8r01-send-hx711.c: 457: temp[0]=0x97;
      0086A2 1E 0C            [ 2] 1343 	ldw	x, (0x0c, sp)
      0086A4 A6 97            [ 1] 1344 	ld	a, #0x97
      0086A6 F7               [ 1] 1345 	ld	(x), a
                                   1346 ;	se8r01-send-hx711.c: 458: temp[1]=0x64;
      0086A7 1E 0A            [ 2] 1347 	ldw	x, (0x0a, sp)
      0086A9 A6 64            [ 1] 1348 	ld	a, #0x64
      0086AB F7               [ 1] 1349 	ld	(x), a
                                   1350 ;	se8r01-send-hx711.c: 459: temp[2]=0x00;
      0086AC 1E 08            [ 2] 1351 	ldw	x, (0x08, sp)
      0086AE 7F               [ 1] 1352 	clr	(x)
                                   1353 ;	se8r01-send-hx711.c: 460: temp[3]=0x01;
      0086AF 1E 06            [ 2] 1354 	ldw	x, (0x06, sp)
      0086B1 A6 01            [ 1] 1355 	ld	a, #0x01
      0086B3 F7               [ 1] 1356 	ld	(x), a
                                   1357 ;	se8r01-send-hx711.c: 461: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_RF_IVGEN, temp,4);
      0086B4 1E 0C            [ 2] 1358 	ldw	x, (0x0c, sp)
      0086B6 4B 04            [ 1] 1359 	push	#0x04
      0086B8 89               [ 2] 1360 	pushw	x
      0086B9 4B 3E            [ 1] 1361 	push	#0x3e
      0086BB CD 81 48         [ 4] 1362 	call	_write_spi_buf
      0086BE 5B 04            [ 2] 1363 	addw	sp, #4
                                   1364 ;	se8r01-send-hx711.c: 463: gtemp[0]=0x2A;
      0086C0 1E 14            [ 2] 1365 	ldw	x, (0x14, sp)
      0086C2 A6 2A            [ 1] 1366 	ld	a, #0x2a
      0086C4 F7               [ 1] 1367 	ld	(x), a
                                   1368 ;	se8r01-send-hx711.c: 464: gtemp[1]=0x04;
      0086C5 1E 12            [ 2] 1369 	ldw	x, (0x12, sp)
      0086C7 A6 04            [ 1] 1370 	ld	a, #0x04
      0086C9 F7               [ 1] 1371 	ld	(x), a
                                   1372 ;	se8r01-send-hx711.c: 465: gtemp[2]=0x00;
      0086CA 1E 10            [ 2] 1373 	ldw	x, (0x10, sp)
      0086CC 7F               [ 1] 1374 	clr	(x)
                                   1375 ;	se8r01-send-hx711.c: 466: gtemp[3]=0x7D;
      0086CD 1E 0E            [ 2] 1376 	ldw	x, (0x0e, sp)
      0086CF A6 7D            [ 1] 1377 	ld	a, #0x7d
      0086D1 F7               [ 1] 1378 	ld	(x), a
                                   1379 ;	se8r01-send-hx711.c: 467: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_TEST_PKDET, gtemp, 4);
      0086D2 1E 14            [ 2] 1380 	ldw	x, (0x14, sp)
      0086D4 4B 04            [ 1] 1381 	push	#0x04
      0086D6 89               [ 2] 1382 	pushw	x
      0086D7 4B 3F            [ 1] 1383 	push	#0x3f
      0086D9 CD 81 48         [ 4] 1384 	call	_write_spi_buf
      0086DC 5B 04            [ 2] 1385 	addw	sp, #4
                                   1386 ;	se8r01-send-hx711.c: 469: rf_switch_bank(iBANK0);
      0086DE 4B 00            [ 1] 1387 	push	#0x00
      0086E0 CD 83 82         [ 4] 1388 	call	_rf_switch_bank
      0086E3 84               [ 1] 1389 	pop	a
      0086E4 5B 15            [ 2] 1390 	addw	sp, #21
      0086E6 81               [ 4] 1391 	ret
                                   1392 ;	se8r01-send-hx711.c: 472: void SE8R01_Init()  
                                   1393 ;	-----------------------------------------
                                   1394 ;	 function SE8R01_Init
                                   1395 ;	-----------------------------------------
      0086E7                       1396 _SE8R01_Init:
      0086E7 52 05            [ 2] 1397 	sub	sp, #5
                                   1398 ;	se8r01-send-hx711.c: 475: SE8R01_Calibration();   
      0086E9 CD 83 9F         [ 4] 1399 	call	_SE8R01_Calibration
                                   1400 ;	se8r01-send-hx711.c: 476: SE8R01_Analog_Init();   
      0086EC CD 85 6B         [ 4] 1401 	call	_SE8R01_Analog_Init
                                   1402 ;	se8r01-send-hx711.c: 480: if (SE8R01_DR_2M==1)
      0086EF CE 00 10         [ 2] 1403 	ldw	x, _SE8R01_DR_2M+0
      0086F2 A3 00 01         [ 2] 1404 	cpw	x, #0x0001
      0086F5 26 07            [ 1] 1405 	jrne	00105$
                                   1406 ;	se8r01-send-hx711.c: 481: {  temp[0]=0b01001111; }     //2MHz,+5dbm
      0086F7 96               [ 1] 1407 	ldw	x, sp
      0086F8 5C               [ 2] 1408 	incw	x
      0086F9 A6 4F            [ 1] 1409 	ld	a, #0x4f
      0086FB F7               [ 1] 1410 	ld	(x), a
      0086FC 20 14            [ 2] 1411 	jra	00106$
      0086FE                       1412 00105$:
                                   1413 ;	se8r01-send-hx711.c: 482: else if  (SE8R01_DR_1M==1)
      0086FE CE 00 12         [ 2] 1414 	ldw	x, _SE8R01_DR_1M+0
      008701 A3 00 01         [ 2] 1415 	cpw	x, #0x0001
      008704 26 07            [ 1] 1416 	jrne	00102$
                                   1417 ;	se8r01-send-hx711.c: 483: {  temp[0]=0b01000111;  }     //1MHz,+5dbm
      008706 96               [ 1] 1418 	ldw	x, sp
      008707 5C               [ 2] 1419 	incw	x
      008708 A6 47            [ 1] 1420 	ld	a, #0x47
      00870A F7               [ 1] 1421 	ld	(x), a
      00870B 20 05            [ 2] 1422 	jra	00106$
      00870D                       1423 00102$:
                                   1424 ;	se8r01-send-hx711.c: 485: {temp[0]=0b01101111;  }     //500K,+5dbm
      00870D 96               [ 1] 1425 	ldw	x, sp
      00870E 5C               [ 2] 1426 	incw	x
      00870F A6 6F            [ 1] 1427 	ld	a, #0x6f
      008711 F7               [ 1] 1428 	ld	(x), a
      008712                       1429 00106$:
                                   1430 ;	se8r01-send-hx711.c: 487: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_RF_SETUP,temp,1);
      008712 96               [ 1] 1431 	ldw	x, sp
      008713 5C               [ 2] 1432 	incw	x
      008714 4B 01            [ 1] 1433 	push	#0x01
      008716 89               [ 2] 1434 	pushw	x
      008717 4B 26            [ 1] 1435 	push	#0x26
      008719 CD 81 48         [ 4] 1436 	call	_write_spi_buf
      00871C 5B 04            [ 2] 1437 	addw	sp, #4
                                   1438 ;	se8r01-send-hx711.c: 489: write_spi_reg(WRITE_REG|iRF_BANK0_EN_AA, 0x01);          //enable auto acc on pip 1
      00871E 4B 01            [ 1] 1439 	push	#0x01
      008720 4B 21            [ 1] 1440 	push	#0x21
      008722 CD 80 CE         [ 4] 1441 	call	_write_spi_reg
      008725 5B 02            [ 2] 1442 	addw	sp, #2
                                   1443 ;	se8r01-send-hx711.c: 490: write_spi_reg(WRITE_REG|iRF_BANK0_EN_RXADDR, 0x01);      //enable pip 1
      008727 4B 01            [ 1] 1444 	push	#0x01
      008729 4B 22            [ 1] 1445 	push	#0x22
      00872B CD 80 CE         [ 4] 1446 	call	_write_spi_reg
      00872E 5B 02            [ 2] 1447 	addw	sp, #2
                                   1448 ;	se8r01-send-hx711.c: 491: write_spi_reg(WRITE_REG|iRF_BANK0_SETUP_AW, 0x02);        //4 byte adress
      008730 4B 02            [ 1] 1449 	push	#0x02
      008732 4B 23            [ 1] 1450 	push	#0x23
      008734 CD 80 CE         [ 4] 1451 	call	_write_spi_reg
      008737 5B 02            [ 2] 1452 	addw	sp, #2
                                   1453 ;	se8r01-send-hx711.c: 492: write_spi_reg(WRITE_REG|iRF_BANK0_SETUP_RETR, 0x08);        //lowest 4 bits 0-15 rt transmisston higest 4 bits 256-4096us Auto Retransmit Delay
      008739 4B 08            [ 1] 1454 	push	#0x08
      00873B 4B 24            [ 1] 1455 	push	#0x24
      00873D CD 80 CE         [ 4] 1456 	call	_write_spi_reg
      008740 5B 02            [ 2] 1457 	addw	sp, #2
                                   1458 ;	se8r01-send-hx711.c: 493: write_spi_reg(WRITE_REG|iRF_BANK0_RF_CH, 40);
      008742 4B 28            [ 1] 1459 	push	#0x28
      008744 4B 25            [ 1] 1460 	push	#0x25
      008746 CD 80 CE         [ 4] 1461 	call	_write_spi_reg
      008749 5B 02            [ 2] 1462 	addw	sp, #2
                                   1463 ;	se8r01-send-hx711.c: 494: write_spi_reg(WRITE_REG|iRF_BANK0_DYNPD, 0x01);          //pipe0 pipe1 enable dynamic payload length data
      00874B 4B 01            [ 1] 1464 	push	#0x01
      00874D 4B 3C            [ 1] 1465 	push	#0x3c
      00874F CD 80 CE         [ 4] 1466 	call	_write_spi_reg
      008752 5B 02            [ 2] 1467 	addw	sp, #2
                                   1468 ;	se8r01-send-hx711.c: 495: write_spi_reg(WRITE_REG|iRF_BANK0_FEATURE, 0x07);        // enable dynamic paload lenght; enbale payload with ack enable w_tx_payload_noack
      008754 4B 07            [ 1] 1469 	push	#0x07
      008756 4B 3D            [ 1] 1470 	push	#0x3d
      008758 CD 80 CE         [ 4] 1471 	call	_write_spi_reg
      00875B 5B 02            [ 2] 1472 	addw	sp, #2
                                   1473 ;	se8r01-send-hx711.c: 496: write_spi_reg(WRITE_REG + CONFIG, 0x3E);
      00875D 4B 3E            [ 1] 1474 	push	#0x3e
      00875F 4B 20            [ 1] 1475 	push	#0x20
      008761 CD 80 CE         [ 4] 1476 	call	_write_spi_reg
      008764 5B 02            [ 2] 1477 	addw	sp, #2
                                   1478 ;	se8r01-send-hx711.c: 497: write_spi_buf(WRITE_REG + TX_ADDR, TX_ADDRESS, ADR_WIDTH);  //from tx
      008766 AE 00 1E         [ 2] 1479 	ldw	x, #_TX_ADDRESS+0
      008769 90 93            [ 1] 1480 	ldw	y, x
      00876B 89               [ 2] 1481 	pushw	x
      00876C 4B 04            [ 1] 1482 	push	#0x04
      00876E 90 89            [ 2] 1483 	pushw	y
      008770 4B 30            [ 1] 1484 	push	#0x30
      008772 CD 81 48         [ 4] 1485 	call	_write_spi_buf
      008775 5B 04            [ 2] 1486 	addw	sp, #4
      008777 85               [ 2] 1487 	popw	x
                                   1488 ;	se8r01-send-hx711.c: 499: write_spi_buf(WRITE_REG + RX_ADDR_P0, TX_ADDRESS, ADR_WIDTH); // Use the same address on the RX device as the TX device write_spi_reg(WRITE_REG + RX_PW_P0, TX_PLOAD_WIDTH); // Select same RX payload width as TX Payload width
      008778 4B 04            [ 1] 1489 	push	#0x04
      00877A 89               [ 2] 1490 	pushw	x
      00877B 4B 2A            [ 1] 1491 	push	#0x2a
      00877D CD 81 48         [ 4] 1492 	call	_write_spi_buf
      008780 5B 04            [ 2] 1493 	addw	sp, #4
                                   1494 ;	se8r01-send-hx711.c: 502: PC_ODR |= (1 << CE);
      008782 AE 50 0A         [ 2] 1495 	ldw	x, #0x500a
      008785 F6               [ 1] 1496 	ld	a, (x)
      008786 AA 10            [ 1] 1497 	or	a, #0x10
      008788 F7               [ 1] 1498 	ld	(x), a
      008789 5B 05            [ 2] 1499 	addw	sp, #5
      00878B 81               [ 4] 1500 	ret
                                   1501 ;	se8r01-send-hx711.c: 508: int main () {
                                   1502 ;	-----------------------------------------
                                   1503 ;	 function main
                                   1504 ;	-----------------------------------------
      00878C                       1505 _main:
      00878C 52 3B            [ 2] 1506 	sub	sp, #59
                                   1507 ;	se8r01-send-hx711.c: 510: UCHAR rx_addr_p1[]  = { 0xd2, 0xf0, 0xf0, 0xf0, 0xf0 };
      00878E 90 96            [ 1] 1508 	ldw	y, sp
      008790 90 5C            [ 2] 1509 	incw	y
      008792 A6 D2            [ 1] 1510 	ld	a, #0xd2
      008794 90 F7            [ 1] 1511 	ld	(y), a
      008796 93               [ 1] 1512 	ldw	x, y
      008797 5C               [ 2] 1513 	incw	x
      008798 A6 F0            [ 1] 1514 	ld	a, #0xf0
      00879A F7               [ 1] 1515 	ld	(x), a
      00879B 93               [ 1] 1516 	ldw	x, y
      00879C 5C               [ 2] 1517 	incw	x
      00879D 5C               [ 2] 1518 	incw	x
      00879E A6 F0            [ 1] 1519 	ld	a, #0xf0
      0087A0 F7               [ 1] 1520 	ld	(x), a
      0087A1 93               [ 1] 1521 	ldw	x, y
      0087A2 A6 F0            [ 1] 1522 	ld	a, #0xf0
      0087A4 E7 03            [ 1] 1523 	ld	(0x0003, x), a
      0087A6 93               [ 1] 1524 	ldw	x, y
      0087A7 A6 F0            [ 1] 1525 	ld	a, #0xf0
      0087A9 E7 04            [ 1] 1526 	ld	(0x0004, x), a
                                   1527 ;	se8r01-send-hx711.c: 511: UCHAR tx_addr[]     = { 0xe1, 0xf0, 0xf0, 0xf0, 0xf0 };
      0087AB 90 96            [ 1] 1528 	ldw	y, sp
      0087AD 72 A9 00 2F      [ 2] 1529 	addw	y, #47
      0087B1 A6 E1            [ 1] 1530 	ld	a, #0xe1
      0087B3 90 F7            [ 1] 1531 	ld	(y), a
      0087B5 93               [ 1] 1532 	ldw	x, y
      0087B6 5C               [ 2] 1533 	incw	x
      0087B7 A6 F0            [ 1] 1534 	ld	a, #0xf0
      0087B9 F7               [ 1] 1535 	ld	(x), a
      0087BA 93               [ 1] 1536 	ldw	x, y
      0087BB 5C               [ 2] 1537 	incw	x
      0087BC 5C               [ 2] 1538 	incw	x
      0087BD A6 F0            [ 1] 1539 	ld	a, #0xf0
      0087BF F7               [ 1] 1540 	ld	(x), a
      0087C0 93               [ 1] 1541 	ldw	x, y
      0087C1 A6 F0            [ 1] 1542 	ld	a, #0xf0
      0087C3 E7 03            [ 1] 1543 	ld	(0x0003, x), a
      0087C5 93               [ 1] 1544 	ldw	x, y
      0087C6 1C 00 04         [ 2] 1545 	addw	x, #0x0004
      0087C9 A6 F0            [ 1] 1546 	ld	a, #0xf0
      0087CB F7               [ 1] 1547 	ld	(x), a
                                   1548 ;	se8r01-send-hx711.c: 515: InitializeSystemClock();
      0087CC CD 81 E4         [ 4] 1549 	call	_InitializeSystemClock
                                   1550 ;	se8r01-send-hx711.c: 516: InitializeUART();
      0087CF CD 82 DE         [ 4] 1551 	call	_InitializeUART
                                   1552 ;	se8r01-send-hx711.c: 518: InitializeSPI ();
      0087D2 CD 81 BC         [ 4] 1553 	call	_InitializeSPI
                                   1554 ;	se8r01-send-hx711.c: 521: memset (tx_payload, 0, sizeof(tx_payload));
      0087D5 96               [ 1] 1555 	ldw	x, sp
      0087D6 1C 00 06         [ 2] 1556 	addw	x, #6
      0087D9 1F 38            [ 2] 1557 	ldw	(0x38, sp), x
      0087DB 16 38            [ 2] 1558 	ldw	y, (0x38, sp)
      0087DD 4B 21            [ 1] 1559 	push	#0x21
      0087DF 4B 00            [ 1] 1560 	push	#0x00
      0087E1 5F               [ 1] 1561 	clrw	x
      0087E2 89               [ 2] 1562 	pushw	x
      0087E3 90 89            [ 2] 1563 	pushw	y
      0087E5 CD 89 3D         [ 4] 1564 	call	_memset
      0087E8 5B 06            [ 2] 1565 	addw	sp, #6
                                   1566 ;	se8r01-send-hx711.c: 524: init_io();                        // Initialize IO port
      0087EA CD 83 57         [ 4] 1567 	call	_init_io
                                   1568 ;	se8r01-send-hx711.c: 525: write_spi_reg(FLUSH_TX,0); // transmit -- send data 
      0087ED 4B 00            [ 1] 1569 	push	#0x00
      0087EF 4B E1            [ 1] 1570 	push	#0xe1
      0087F1 CD 80 CE         [ 4] 1571 	call	_write_spi_reg
      0087F4 5B 02            [ 2] 1572 	addw	sp, #2
                                   1573 ;	se8r01-send-hx711.c: 526: readstatus = read_spi_reg(CONFIG);
      0087F6 4B 00            [ 1] 1574 	push	#0x00
      0087F8 CD 81 0A         [ 4] 1575 	call	_read_spi_reg
      0087FB 5B 01            [ 2] 1576 	addw	sp, #1
                                   1577 ;	se8r01-send-hx711.c: 527: UARTPrintF("config = \n\r");
      0087FD AE 88 CF         [ 2] 1578 	ldw	x, #___str_0+0
      008800 88               [ 1] 1579 	push	a
      008801 89               [ 2] 1580 	pushw	x
      008802 CD 82 79         [ 4] 1581 	call	_UARTPrintF
      008805 5B 02            [ 2] 1582 	addw	sp, #2
      008807 84               [ 1] 1583 	pop	a
                                   1584 ;	se8r01-send-hx711.c: 528: print_UCHAR_hex(readstatus);
      008808 88               [ 1] 1585 	push	a
      008809 CD 82 90         [ 4] 1586 	call	_print_UCHAR_hex
      00880C 84               [ 1] 1587 	pop	a
                                   1588 ;	se8r01-send-hx711.c: 529: readstatus = read_spi_reg(STATUS);
      00880D 4B 07            [ 1] 1589 	push	#0x07
      00880F CD 81 0A         [ 4] 1590 	call	_read_spi_reg
      008812 5B 01            [ 2] 1591 	addw	sp, #1
                                   1592 ;	se8r01-send-hx711.c: 530: UARTPrintF("status = \n\r");
      008814 AE 88 DB         [ 2] 1593 	ldw	x, #___str_1+0
      008817 88               [ 1] 1594 	push	a
      008818 89               [ 2] 1595 	pushw	x
      008819 CD 82 79         [ 4] 1596 	call	_UARTPrintF
      00881C 5B 02            [ 2] 1597 	addw	sp, #2
      00881E 84               [ 1] 1598 	pop	a
                                   1599 ;	se8r01-send-hx711.c: 531: print_UCHAR_hex(readstatus);
      00881F 88               [ 1] 1600 	push	a
      008820 CD 82 90         [ 4] 1601 	call	_print_UCHAR_hex
      008823 84               [ 1] 1602 	pop	a
                                   1603 ;	se8r01-send-hx711.c: 533: SE8R01_Init();
      008824 CD 86 E7         [ 4] 1604 	call	_SE8R01_Init
                                   1605 ;	se8r01-send-hx711.c: 537: while (1) {
      008827                       1606 00108$:
                                   1607 ;	se8r01-send-hx711.c: 540: ADC_CR1 |= ADC_ADON; // ADC ON
      008827 72 10 54 01      [ 1] 1608 	bset	0x5401, #0
                                   1609 ;	se8r01-send-hx711.c: 541: ADC_CSR |= ((0x0F)&4); // select channel = 4 = PD3
      00882B AE 54 00         [ 2] 1610 	ldw	x, #0x5400
      00882E F6               [ 1] 1611 	ld	a, (x)
      00882F AA 04            [ 1] 1612 	or	a, #0x04
      008831 F7               [ 1] 1613 	ld	(x), a
                                   1614 ;	se8r01-send-hx711.c: 542: ADC_CR2 |= ADC_ALIGN; // Right Aligned Data
      008832 AE 54 02         [ 2] 1615 	ldw	x, #0x5402
      008835 F6               [ 1] 1616 	ld	a, (x)
      008836 AA 08            [ 1] 1617 	or	a, #0x08
      008838 F7               [ 1] 1618 	ld	(x), a
                                   1619 ;	se8r01-send-hx711.c: 543: ADC_CR1 |= ADC_ADON; // start conversion 
      008839 72 10 54 01      [ 1] 1620 	bset	0x5401, #0
                                   1621 ;	se8r01-send-hx711.c: 544: while(((ADC_CSR)&(1<<7))== 0); // Wait till EOC
      00883D                       1622 00101$:
      00883D AE 54 00         [ 2] 1623 	ldw	x, #0x5400
      008840 F6               [ 1] 1624 	ld	a, (x)
      008841 48               [ 1] 1625 	sll	a
      008842 24 F9            [ 1] 1626 	jrnc	00101$
                                   1627 ;	se8r01-send-hx711.c: 545: tx_payload[2] = (unsigned int)ADC_DRH;
      008844 16 38            [ 2] 1628 	ldw	y, (0x38, sp)
      008846 72 A9 00 02      [ 2] 1629 	addw	y, #0x0002
      00884A AE 54 04         [ 2] 1630 	ldw	x, #0x5404
      00884D F6               [ 1] 1631 	ld	a, (x)
      00884E 0F 36            [ 1] 1632 	clr	(0x36, sp)
      008850 90 F7            [ 1] 1633 	ld	(y), a
                                   1634 ;	se8r01-send-hx711.c: 546: tx_payload[3] = (unsigned int)ADC_DRL;
      008852 16 38            [ 2] 1635 	ldw	y, (0x38, sp)
      008854 72 A9 00 03      [ 2] 1636 	addw	y, #0x0003
      008858 AE 54 05         [ 2] 1637 	ldw	x, #0x5405
      00885B F6               [ 1] 1638 	ld	a, (x)
      00885C 0F 34            [ 1] 1639 	clr	(0x34, sp)
      00885E 90 F7            [ 1] 1640 	ld	(y), a
                                   1641 ;	se8r01-send-hx711.c: 551: ADC_CR1 &= ~(1<<0); // ADC Stop Conversion
      008860 AE 54 01         [ 2] 1642 	ldw	x, #0x5401
      008863 F6               [ 1] 1643 	ld	a, (x)
      008864 A4 FE            [ 1] 1644 	and	a, #0xfe
      008866 F7               [ 1] 1645 	ld	(x), a
                                   1646 ;	se8r01-send-hx711.c: 552: ampere &= 0x03ff; // 0 bits resolution so above 0x0400 is nothing
      008867 7B 28            [ 1] 1647 	ld	a, (0x28, sp)
      008869 6B 3B            [ 1] 1648 	ld	(0x3b, sp), a
      00886B 7B 27            [ 1] 1649 	ld	a, (0x27, sp)
      00886D A4 03            [ 1] 1650 	and	a, #0x03
      00886F 6B 27            [ 1] 1651 	ld	(0x27, sp), a
      008871 7B 3B            [ 1] 1652 	ld	a, (0x3b, sp)
      008873 6B 28            [ 1] 1653 	ld	(0x28, sp), a
                                   1654 ;	se8r01-send-hx711.c: 557: tx_payload[0] = 0xac; //first two is unique ID for current sensor
      008875 1E 38            [ 2] 1655 	ldw	x, (0x38, sp)
      008877 A6 AC            [ 1] 1656 	ld	a, #0xac
      008879 F7               [ 1] 1657 	ld	(x), a
                                   1658 ;	se8r01-send-hx711.c: 558: tx_payload[1] = 0xcc;
      00887A 1E 38            [ 2] 1659 	ldw	x, (0x38, sp)
      00887C 5C               [ 2] 1660 	incw	x
      00887D A6 CC            [ 1] 1661 	ld	a, #0xcc
      00887F F7               [ 1] 1662 	ld	(x), a
                                   1663 ;	se8r01-send-hx711.c: 561: write_spi_buf(iRF_CMD_WR_TX_PLOAD, tx_payload, 4);
      008880 1E 38            [ 2] 1664 	ldw	x, (0x38, sp)
      008882 4B 04            [ 1] 1665 	push	#0x04
      008884 89               [ 2] 1666 	pushw	x
      008885 4B A0            [ 1] 1667 	push	#0xa0
      008887 CD 81 48         [ 4] 1668 	call	_write_spi_buf
      00888A 5B 04            [ 2] 1669 	addw	sp, #4
                                   1670 ;	se8r01-send-hx711.c: 562: write_spi_reg(WRITE_REG+STATUS, 0xff);
      00888C 4B FF            [ 1] 1671 	push	#0xff
      00888E 4B 27            [ 1] 1672 	push	#0x27
      008890 CD 80 CE         [ 4] 1673 	call	_write_spi_reg
      008893 5B 02            [ 2] 1674 	addw	sp, #2
                                   1675 ;	se8r01-send-hx711.c: 569: for (x1 = 0; x1 < 50; ++x1)
      008895 5F               [ 1] 1676 	clrw	x
      008896 1F 2D            [ 2] 1677 	ldw	(0x2d, sp), x
      008898                       1678 00117$:
      008898 1E 2D            [ 2] 1679 	ldw	x, (0x2d, sp)
      00889A A3 00 32         [ 2] 1680 	cpw	x, #0x0032
      00889D 2F 03            [ 1] 1681 	jrslt	00158$
      00889F CC 88 27         [ 2] 1682 	jp	00108$
      0088A2                       1683 00158$:
                                   1684 ;	se8r01-send-hx711.c: 570: for (y1 = 0; y1 < 50; ++y1)
      0088A2 5F               [ 1] 1685 	clrw	x
      0088A3 1F 2B            [ 2] 1686 	ldw	(0x2b, sp), x
      0088A5                       1687 00114$:
      0088A5 1E 2B            [ 2] 1688 	ldw	x, (0x2b, sp)
      0088A7 A3 00 32         [ 2] 1689 	cpw	x, #0x0032
      0088AA 2E 19            [ 1] 1690 	jrsge	00118$
                                   1691 ;	se8r01-send-hx711.c: 571: for (z1 = 0; z1 < 50; ++z1)
      0088AC 5F               [ 1] 1692 	clrw	x
      0088AD 1F 29            [ 2] 1693 	ldw	(0x29, sp), x
      0088AF                       1694 00111$:
      0088AF 1E 29            [ 2] 1695 	ldw	x, (0x29, sp)
      0088B1 A3 00 32         [ 2] 1696 	cpw	x, #0x0032
      0088B4 2E 08            [ 1] 1697 	jrsge	00115$
                                   1698 ;	se8r01-send-hx711.c: 572: __asm__("nop");
      0088B6 9D               [ 1] 1699 	nop
                                   1700 ;	se8r01-send-hx711.c: 571: for (z1 = 0; z1 < 50; ++z1)
      0088B7 1E 29            [ 2] 1701 	ldw	x, (0x29, sp)
      0088B9 5C               [ 2] 1702 	incw	x
      0088BA 1F 29            [ 2] 1703 	ldw	(0x29, sp), x
      0088BC 20 F1            [ 2] 1704 	jra	00111$
      0088BE                       1705 00115$:
                                   1706 ;	se8r01-send-hx711.c: 570: for (y1 = 0; y1 < 50; ++y1)
      0088BE 1E 2B            [ 2] 1707 	ldw	x, (0x2b, sp)
      0088C0 5C               [ 2] 1708 	incw	x
      0088C1 1F 2B            [ 2] 1709 	ldw	(0x2b, sp), x
      0088C3 20 E0            [ 2] 1710 	jra	00114$
      0088C5                       1711 00118$:
                                   1712 ;	se8r01-send-hx711.c: 569: for (x1 = 0; x1 < 50; ++x1)
      0088C5 1E 2D            [ 2] 1713 	ldw	x, (0x2d, sp)
      0088C7 5C               [ 2] 1714 	incw	x
      0088C8 1F 2D            [ 2] 1715 	ldw	(0x2d, sp), x
      0088CA 20 CC            [ 2] 1716 	jra	00117$
      0088CC 5B 3B            [ 2] 1717 	addw	sp, #59
      0088CE 81               [ 4] 1718 	ret
                                   1719 	.area CODE
      0088CF                       1720 ___str_0:
      0088CF 63 6F 6E 66 69 67 20  1721 	.ascii "config = "
             3D 20
      0088D8 0A                    1722 	.db 0x0A
      0088D9 0D                    1723 	.db 0x0D
      0088DA 00                    1724 	.db 0x00
      0088DB                       1725 ___str_1:
      0088DB 73 74 61 74 75 73 20  1726 	.ascii "status = "
             3D 20
      0088E4 0A                    1727 	.db 0x0A
      0088E5 0D                    1728 	.db 0x0D
      0088E6 00                    1729 	.db 0x00
                                   1730 	.area INITIALIZER
      00895C                       1731 __xinit__SE8R01_DR_2M:
      00895C 00 00                 1732 	.dw #0x0000
      00895E                       1733 __xinit__SE8R01_DR_1M:
      00895E 00 00                 1734 	.dw #0x0000
      008960                       1735 __xinit__SE8R01_DR_500K:
      008960 00 01                 1736 	.dw #0x0001
      008962                       1737 __xinit__pload_width_now:
      008962 00 00                 1738 	.dw #0x0000
      008964                       1739 __xinit__newdata:
      008964 00 00                 1740 	.dw #0x0000
      008966                       1741 __xinit__signal_lv:
      008966 00                    1742 	.db #0x00	;  0
      008967                       1743 __xinit__pip:
      008967 00 00                 1744 	.dw #0x0000
      008969                       1745 __xinit__status:
      008969 00                    1746 	.db #0x00	; 0
      00896A                       1747 __xinit__TX_ADDRESS:
      00896A B3                    1748 	.db #0xB3	; 179
      00896B 43                    1749 	.db #0x43	; 67	'C'
      00896C 10                    1750 	.db #0x10	; 16
      00896D 10                    1751 	.db #0x10	; 16
      00896E                       1752 __xinit__ADDRESS2:
      00896E B1                    1753 	.db #0xB1	; 177
      00896F                       1754 __xinit__ADDRESS3:
      00896F B2                    1755 	.db #0xB2	; 178
      008970                       1756 __xinit__ADDRESS4:
      008970 B3                    1757 	.db #0xB3	; 179
      008971                       1758 __xinit__ADDRESS5:
      008971 B4                    1759 	.db #0xB4	; 180
      008972                       1760 __xinit__ADDRESS1:
      008972 B0                    1761 	.db #0xB0	; 176
      008973 43                    1762 	.db #0x43	; 67	'C'
      008974 10                    1763 	.db #0x10	; 16
      008975 10                    1764 	.db #0x10	; 16
      008976                       1765 __xinit__ADDRESS0:
      008976 34                    1766 	.db #0x34	; 52	'4'
      008977 43                    1767 	.db #0x43	; 67	'C'
      008978 10                    1768 	.db #0x10	; 16
      008979 10                    1769 	.db #0x10	; 16
      00897A                       1770 __xinit__rx_buf:
      00897A 00                    1771 	.db #0x00	; 0
      00897B 00                    1772 	.db 0x00
      00897C 00                    1773 	.db 0x00
      00897D 00                    1774 	.db 0x00
      00897E 00                    1775 	.db 0x00
      00897F 00                    1776 	.db 0x00
      008980 00                    1777 	.db 0x00
      008981 00                    1778 	.db 0x00
      008982 00                    1779 	.db 0x00
      008983 00                    1780 	.db 0x00
      008984 00                    1781 	.db 0x00
      008985 00                    1782 	.db 0x00
      008986 00                    1783 	.db 0x00
      008987 00                    1784 	.db 0x00
      008988 00                    1785 	.db 0x00
      008989 00                    1786 	.db 0x00
      00898A 00                    1787 	.db 0x00
      00898B 00                    1788 	.db 0x00
      00898C 00                    1789 	.db 0x00
      00898D 00                    1790 	.db 0x00
      00898E 00                    1791 	.db 0x00
      00898F 00                    1792 	.db 0x00
      008990 00                    1793 	.db 0x00
      008991 00                    1794 	.db 0x00
      008992 00                    1795 	.db 0x00
      008993 00                    1796 	.db 0x00
      008994 00                    1797 	.db 0x00
      008995 00                    1798 	.db 0x00
      008996 00                    1799 	.db 0x00
      008997 00                    1800 	.db 0x00
      008998 00                    1801 	.db 0x00
      008999 00                    1802 	.db 0x00
      00899A                       1803 __xinit__tx_buf:
      00899A 00                    1804 	.db #0x00	; 0
      00899B 00                    1805 	.db 0x00
      00899C 00                    1806 	.db 0x00
      00899D 00                    1807 	.db 0x00
      00899E 00                    1808 	.db 0x00
      00899F 00                    1809 	.db 0x00
      0089A0 00                    1810 	.db 0x00
      0089A1 00                    1811 	.db 0x00
      0089A2 00                    1812 	.db 0x00
      0089A3 00                    1813 	.db 0x00
      0089A4 00                    1814 	.db 0x00
      0089A5 00                    1815 	.db 0x00
      0089A6 00                    1816 	.db 0x00
      0089A7 00                    1817 	.db 0x00
      0089A8 00                    1818 	.db 0x00
      0089A9 00                    1819 	.db 0x00
      0089AA 00                    1820 	.db 0x00
      0089AB 00                    1821 	.db 0x00
      0089AC 00                    1822 	.db 0x00
      0089AD 00                    1823 	.db 0x00
      0089AE 00                    1824 	.db 0x00
      0089AF 00                    1825 	.db 0x00
      0089B0 00                    1826 	.db 0x00
      0089B1 00                    1827 	.db 0x00
      0089B2 00                    1828 	.db 0x00
      0089B3 00                    1829 	.db 0x00
      0089B4 00                    1830 	.db 0x00
      0089B5 00                    1831 	.db 0x00
      0089B6 00                    1832 	.db 0x00
      0089B7 00                    1833 	.db 0x00
      0089B8 00                    1834 	.db 0x00
      0089B9 00                    1835 	.db 0x00
                                   1836 	.area CABS (ABS)
