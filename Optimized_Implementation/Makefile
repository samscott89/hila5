# Makefile
# 2017-09-23  Markku-Juhani O. Saarinen <mjos@iki.fi>
# (Optimized Implementation)

BIN	= genkat_opt
OBJS	= kem.o hila5_sha3_opt.o ms_ntt.o ms_ntt_const.o \
	../KAT/src/rng.o ../KAT/src/PQCgenKAT_kem.o

CC	= gcc
CFLAGS	= -std=c99 -Wall -Ofast
LIBS	= -lcrypto
LDFLAGS	=
INCS	= -I.

$(BIN): $(OBJS)
	$(CC) $(LDFLAGS) -o $(BIN) $(OBJS) $(LIBS)

test:	$(BIN)
	./$(BIN)
	@echo "== KAT DIFFERENCE =="
	diff PQCkemKAT_1824.rsp ../KAT/PQCkemKAT_1824.rsp
	@echo "== CLEANUP =="
	make clean

.c.o:
	$(CC) $(CFLAGS) $(INCS) -c $< -o $@

clean:
	rm -rf $(OBJS) $(BIN) PQCkemKAT_1824.*
