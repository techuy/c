CFLAGS  = -std=c99
CFLAGS += -g
CFLAGS += -Wall
CFLAGS += -Wextra
CFLAGS += -pedantic
CFLAGS += -Werror

VFLAGS  = --quiet
VFLAGS += --tool=memcheck
VFLAGS += --leak-check=full
VFLAGS += --error-exitcode=1

test: tests.out
	@./tests.out

memcheck: tests.out
	@valgrind $(VFLAGS) ./tests.out
	@echo "Memory check passed"

clean:
	rm -rf *.o *.out *.out.dSYM

tests.out: test/test_collatz_conjecture.c src/collatz_conjecture.c src/collatz_conjecture.h
	@echo Compiling $@
	@$(CC) $(CFLAGS) src/collatz_conjecture.c test/vendor/unity.c test/test_collatz_conjecture.c -o tests.out
