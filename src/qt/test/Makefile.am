include $(top_srcdir)/src/Makefile.include

AM_CPPFLAGS += -I$(top_srcdir)/src \
  -I$(top_srcdir)/src/qt \
  -I$(top_builddir)/src/qt \
  $(PROTOBUF_CFLAGS) \
    $(QR_CFLAGS)
bin_PROGRAMS = test_patacoin-qt
TESTS = test_patacoin-qt

TEST_QT_MOC_CPP = moc_uritests.cpp

if ENABLE_WALLET
TEST_QT_MOC_CPP += moc_paymentservertests.cpp
endif

TEST_QT_H = \
  uritests.h \
  paymentrequestdata.h \
  paymentservertests.h

BUILT_SOURCES = $(TEST_QT_MOC_CPP)

test_patacoin_qt_CPPFLAGS = $(AM_CPPFLAGS) $(QT_INCLUDES) $(QT_TEST_INCLUDES)

test_patacoin_qt_SOURCES = \
  test_main.cpp \
  uritests.cpp \
  $(TEST_QT_H)
if ENABLE_WALLET
test_patacoin_qt_SOURCES += \
  paymentservertests.cpp
endif

nodist_test_patacoin_qt_SOURCES = $(TEST_QT_MOC_CPP)

test_patacoin_qt_LDADD = $(LIBPATACOINQT) $(LIBPATACOIN_SERVER)
if ENABLE_WALLET
test_patacoin_qt_LDADD += $(LIBPATACOIN_WALLET)
endif
test_patacoin_qt_LDADD += $(LIBPATACOIN_CLI) $(LIBPATACOIN_COMMON) $(LIBLEVELDB) \
  $(LIBMEMENV) $(BOOST_LIBS) $(QT_DBUS_LIBS) $(QT_TEST_LIBS) $(QT_LIBS) \
  $(QR_LIBS) $(PROTOBUF_LIBS) $(BDB_LIBS)

CLEANFILES = $(BUILT_SOURCES) *.gcda *.gcno
