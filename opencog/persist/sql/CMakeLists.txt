# Uncomment this if SQL is installed.
# ADD_DEFINITIONS(-DHAVE_SQL_STORAGE)

ADD_LIBRARY (sql-support
	AtomStorage
	SQLBackingStore
)

ADD_DEPENDENCIES(sql-support opencog_atom_types)

TARGET_LINK_LIBRARIES(sql-support
	atomspace
	${ODBC_LIBRARIES}
)

INSTALL (FILES
	AtomStorage.h
	SQLBackingStore.h
	DESTINATION "include/opencog/persist/sql"
)

INSTALL (TARGETS sql-support
    DESTINATION "lib${LIB_DIR_SUFFIX}/opencog"
)

ADD_SUBDIRECTORY (odbc)
ADD_SUBDIRECTORY (postgres)
