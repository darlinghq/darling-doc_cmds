project(doc_cmds)

add_compile_options(
	-nostdinc
	-Wno-incompatible-pointer-types
	-Wno-format
)

add_definitions(
	-D__FBSDID=__RCSID
)

add_darling_executable(checknr checknr/checknr.c)
add_darling_executable(colcrt colcrt/colcrt.c)
add_darling_executable(makewhatis makewhatis/makewhatis.c)
target_link_libraries(makewhatis z)

install(TARGETS checknr colcrt DESTINATION libexec/darling/usr/bin)
install(TARGETS makewhatis DESTINATION libexec/darling/usr/libexec)
install(FILES intro.1 checknr/checknr.1 colcrt/colcrt.1 DESTINATION libexec/darling/usr/share/man/man1)
install(FILES makewhatis/makewhatis.local.sh
	DESTINATION libexec/darling/usr/libexec
	RENAME makewhatis.local
	PERMISSIONS OWNER_READ OWNER_WRITE  OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
)
install(FILES makewhatis/makewhatis.8 makewhatis/makewhatis.local.8 DESTINATION libexec/darling/usr/share/man/man8)
