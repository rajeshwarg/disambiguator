
#ILOGINSTALLDIR=/data/patentdata/ILOG/CPLEX_Studio124
ILOGINSTALLDIR=/Users/daviddoolin/Applications/IBM/ILOG/CPLEX_Studio124
CPLEXINCLUDE=$(ILOGINSTALLDIR)/cplex/include
CONCERTINCLUDE=$(ILOGINSTALLDIR)/concert/include

# Linux server
#CPLEXLIB=$(ILOGINSTALLDIR)/cplex/lib/x86-64_sles10_4.1/static_pic
#CONCERTLIB=$(ILOGINSTALLDIR)/concert/lib/x86-64_sles10_4.1/static_pic
# Local macbook
CPLEXLIB=$(ILOGINSTALLDIR)/cplex/lib/x86-64_darwin9_gcc4.0/static_pic
CONCERTLIB=$(ILOGINSTALLDIR)/concert/lib/x86-64_darwin9_gcc4.0/static_pic

INCLUDES = -I/usr/local/include -I$(CPLEXINCLUDE) -I$(CONCERTINCLUDE) -I../include -I/opt/local/include -I../src



#CXXFLAGS =  -Wall -Wextra -ansi -Wignored-qualifiers # -pedantic -Wno-unused-parameter -Wno-uninitialized # -Wno-ignored-qualifiers
AM_CXXFLAGS = -std=c++11 -O0 -g -Wall -Wextra -Wformat-zero-length -Wno-unused-parameter -Wno-uninitialized # -pedantic -ansi
#CXXFLAGS = $(AM_CXXFLAGS)

LDADD = ../src/libdisambiguation.a
AM_LDFLAGS = $(shell cppunit-config --libs) -L$(CPLEXLIB) -lilocplex -lcplex -L$(CONCERTLIB) -lconcert
#AM_CXXFLAGS = $(shell cppunit-config --libs) -L$(CPLEXLIB) -lilocplex -lcplex -L$(CONCERTLIB) -lconcert


TESTS =  typedefs record blocking attribute stringmanipulator \
	comparators comparesimilarities strcmp95 rarenames engineconfig           \
	abbreviation misspell namecompare jwcmp similarity clusterhead cluster engine \
	training ratios fetchrecords assigneecomparison clusterinfo ratiocomponent \
	coauthor qp compare testfake postprocess

bin_PROGRAMS = $(TESTS)

%.o: %.cpp
	g++ $(AM_CXXFLAGS) $(INCLUDES) -D$*_STANDALONE -c $<

COMMON = testdata.cpp testutils.cpp

#fake_SOURCES = fake.cpp $(COMMON)
testfake_SOURCES = testfake.cpp fake.cpp $(COMMON)
ratiocomponent_SOURCES = test_ratiocomponent.cpp fake.cpp $(COMMON)
engine_SOURCES = test_engine.cpp $(COMMON)
typedefs_SOURCES = test_typedefs.cpp
record_SOURCES = test_record.cpp $(COMMON)
cluster_SOURCES = test_cluster.cpp fake.cpp $(COMMON)
clusterinfo_SOURCES = test_clusterinfo.cpp fake.cpp $(COMMON)
training_SOURCES = test_training.cpp fake.cpp $(COMMON)
clusterhead_SOURCES = test_clusterhead.cpp $(COMMON)
attribute_SOURCES = test_attribute.cpp fake.cpp $(COMMON)
fetchrecords_SOURCES = test_fetch_records.cpp $(COMMON)
assigneecomparison_SOURCES = test_assignee_comparison.cpp fake.cpp $(COMMON)
coauthor_SOURCES = test_coauthor.cpp fake.cpp $(COMMON)
comparators_SOURCES = test_comparators.cpp $(COMMON)
rarenames_SOURCES = test_rarenames.cpp $(COMMON)
jwcmp_SOURCES = test_jwcmp.cpp $(COMMON)
ratios_SOURCES = test_ratios.cpp fake.cpp $(COMMON)
similarity_SOURCES = test_similarity.cpp $(COMMON)
abbreviation_SOURCES = test_abbreviation.cpp
misspell_SOURCES = test_misspell.cpp $(COMMON)
namecompare_SOURCES = test_namecompare.cpp $(COMMON)
engineconfig_SOURCES = test_engineconfig.cpp $(COMMON)
comparesimilarities_SOURCES = test_compare.cpp

blocking_SOURCES = test_blocking.cpp $(COMMON) fake.cpp 
blocking_LDADD = ../src/libdisambiguation.a -L$(CPLEXLIB) -lilocplex -lcplex -L$(CONCERTLIB) -lconcert 

stringmanipulator_SOURCES = test_string_manipulator.cpp $(COMMON)
strcmp95_SOURCES = test_strcmp95.cpp $(COMMON)
qp_SOURCES = test_qp.cpp $(COMMON)
compare_SOURCES = test_compare.cpp $(COMMON)
postprocess_SOURCES = test_postprocess.cpp $(COMMON)

relink:
	rm -rf $(TESTS)

