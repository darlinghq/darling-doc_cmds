project(doc_cmds)

add_darling_executable(checknr checknr/checknr.c)
add_darling_executable(colcrt colcrt/colcrt.c)
add_darling_executable(makewhatis makewhatis/makewhatis.c)

install(TARGETS checknr colcrt DESTINATION libexec/darling/usr/bin)
install(TARGETS makewhatis DESTINATION libexec/darling/usr/libexec)
install(FILES intro.1 checknr/checknr.1 colcrt/colcrt.1 DESTINATION libexec/darling/usr/share/man/man1)
install(FILES makewhatis/makewhatis.local.sh
	DESTINATION libexec/darling/usr/libexec
	PERMISSIONS USER_READ USER_WRITE  USER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
)
install(FILES makewhatis/makewhatis.8 makewhatis/makewhatis.local.8 DESTINATION libexec/darling/usr/share/man/man8)
