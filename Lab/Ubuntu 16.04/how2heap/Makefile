BASE = first_fit calc_tcache_idx
V2.23 = glibc_2.23/fastbin_dup_into_stack glibc_2.23/fastbin_dup_consolidate glibc_2.23/unsafe_unlink glibc_2.23/house_of_spirit glibc_2.23/poison_null_byte glibc_2.23/house_of_lore glibc_2.23/overlapping_chunks glibc_2.23/overlapping_chunks_2 glibc_2.23/house_of_force glibc_2.23/large_bin_attack glibc_2.23/unsorted_bin_attack glibc_2.23/unsorted_bin_into_stack glibc_2.23/house_of_einherjar glibc_2.23/house_of_orange glibc_2.23/house_of_roman glibc_2.23/mmap_overlapping_chunks glibc_2.23/fastbin_dup
PROGRAMS = $(BASE) $(V2.23)
CFLAGS += -std=c99 -g -no-pie
LDLIBS += -ldl

# Convenience to auto-call mcheck before the first malloc()
#CFLAGS += -lmcheck

all: $(PROGRAMS)
clean:
	rm -f $(PROGRAMS)

define test_poc =
echo $(poc)
for i in $$(seq 0 4);\
do\
	LIBC_FATAL_STDERR_=1 $(poc) 1>/dev/null 2>&1 0>&1;\
	if [ "$$?" = "0" ]; then break; fi;\
	if [ "$$i" = "4" ]; then exit 1; fi;\
done
echo "success"
endef

#if [ "$$i" == "5" ]; then exit 1; fi;\

test: $(PROGRAMS)
	@if [ -z "$(target)" ] || [ -z "$(V$(target))" ];\
	then echo "run 'make test target=<target_version>' to test existing techniques"; exit 1; fi;

	@$(foreach poc,$(V$(target)),$(call test_poc,$(poc));)
