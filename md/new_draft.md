# Introduction

Our names are Werner Krause and Dag Tanneberg. We graduated in
Political Science with a focus on Comparative Politics.
Currently, we are pursuing our doctoral degrees at the
research department "Democracy and Democratization"
located at the Berlin Social Science Center WZB, Germany.

Much of the research at our department revolves around
political competition, elections, and the dynamics of
democratic government. Already in the early 1990s senior
fellows decided to set up a permanent infrastructure
offering data on elections and governments to all department
members in a standardized and easily accessible format.
Originally, the data were used to observe and analyze the
consolidation processes in Eastern and Middle European
democracies. The project has since grown into a
database that includes more than eighty countries around
the world between 1945 and today.

The database keeps track of diverse aspects of political
competition. For instance, we code lower house and
presidential election results, government duration, their
size and composition as well as the ebb and flow of
electoral alliances between political parties. Department
members may output either raw data and digitized copies of
our primary sources or summary statistics like turnout, the
effective number of parties, measurements of
disproportionality or government stability.

Back in 2011 respectively 2008 we were recruited as RAs to
continue this longstanding project. We introduced several
substantive and technological innovations
into the database that sum to more streamlined and less
error prone coding and data management routines. It was our
goal to ensure transparency and reproducibility from the
point of coding of individual parties in single elections to
the point of generating summary statistics on every election
covered between 1945 and today.

Broadly speaking, we understand reproducibility as the
responsibility of researchers to provide sufficient detail
on their work such that others using the same data and
methods will be able to replicate their results -- be those
single statistics, graphs, and tables or entire articles.
Results that cannot be reproduced are neither open to
critique nor revision. In effect, they are unscientific.

In the context of our database reproducibility receives an
even more demanding meaning. Since the quality of the data
stored in our database affects numerous ongoing projects in-
_and_ outside of our department every single piece of
information should be reproducible. The challenge is thus to
make the acquisition and coding of primary data as
transparent to others as the standardized output we provide
for secondary analyses.

# Workflow

!["Workflow diagram of our database"](./GovElec_Workflow_May2k16.png)

Our workflow has four separate steps. Data first have to be hand coded. Second,
codings go through different human supervised and automated consistency checks. Third, the newly generated data are processed before storing them in our back-end database. Finally, information can be outputted from our database. All
steps can be fulfilled independently of each other.

Our team consists of one student assistant, two research fellows and one senior researcher. While the first is responsible for the coding and input of the data as well as some basic consistency checks, automated data tests and processing are maintained by our research fellows. In general, we are concerned with three basic challenges while collecting, coding and processing our data: reduce coding errors, maintain a high degree of intercoder reliability and provide transparency on the entire decision-making process. The following
paragraphs will focus on these challenges.

The first decision to be made is whether a new observation needs to be added to the dataset. For that purpose we collect all upcoming elections and government formations for our sample of 82 countries in the world. Once a new data entry is necessary, sources are identified by the coder that contain information on party histories, election results and/or government events. Evaluating the quality of the source is essential since only documents which provide us with information as disaggregated as possible guarantee that we can reliably and correctly code the respective data. For that purpose, a list of high quality sources is included in a codebook that also lists all coding decisions. If, due to lack of reliable sources, information from non-identified documents is used, these data entries are flagged in order to identify more reliable sources in the future. This is for instance the case if election results are documented as aggregated vote and seat shares instead of as absolute numbers. Once a source has been identified, the data is coded manually following the rules of the codebook.

In the following the data is entered into a _Microsoft Access_ Database and the source (including the coding decisions) is saved on a server which can be assessed by all users of the output-datasets. Although MS Access is not a free software-tool, it provides a) a relational database that can be easily maintained by research fellows and b) a user interface that makes the data entry clear and easily understandable. Hence, due its form-based structure the _MS Access_ interface serves as a standardized coding structure that reduces error and increases intercoder reliability. Moreover, the _MS Access_ interface allows to perform basic consistency checks which enable the coder to easily evaluate the reliability of sources. To give two examples: One such check routine is to verify that the sum of the documented number of votes equals the total number of valid votes given in the source. Another consistency check tests if the seat share of all parties in a coalition government does correspond to the documented type of government. If one of these checks fails, new sources have to be considered in order to reach an error-free documentation of the data.

After the data entry has been finalized, it is automatically exported to a PostgreSQL-Database which allows us to store the entire dataset and to put it under version control using _Git_. Changes to the dataset are thus documented on a daily basis. At the same time, automated, more complex consistency checks are performed by making use of the open source statistic software _R_ (https://www.r-project.org/). Based on these, pdf reports are created using the _R_-package _knitr_ (http://yihui.name/knitr/) and send to one of our research
fellows. These reports document all new data entries, all data changes and failed consistency checks. Due to this, the work of our coder can easily be tracked by experienced colleagues and possible coding errors are spotted immediately.

After that, manual error coding is conducted and documented. In spite of our aspiration to exclusively collect data from high quality sources certain inconsistencies cannot be avoided. For example, sometimes we cannot identify the seats controlled by a coalition government in the parliament since its member parties have contested the previous election in different electoral pacts for which no individual party seat shares are provided. These and other cases are identified by the automated R-scripts. However due to the diversity of inconsistencies and reasons for them, they are manually flagged and documented.

Following this, the R-scripts process the data, i.e. they join different tables and drop irrelevant variables, in order to provide a raw dataset that includes basically all data entries without any additional measures. Based on this raw dataset, further additional calculations are conducted in order to provide an extended dataset that includes common measures in the discipline (like turnout, the effective number of parties, measurements of
disproportionality or government stability).

After these steps are finished, both datasets are publicly accessible via Shiny-Interface (http://shiny.rstudio.com/) which allows the end-user to browse and download the raw as well as the extended dataset. In addition the aforementioned codebook of the database can be downloaded in order to guarantee a high transparency of coding decisions.

<font color="red">Words: 844/800</font>

# Pain points

One pain point is to manually code and document cases that do not fit our pre-defined coding scheme. That is for instance the case for our documentation of political parties and their election results. In many countries, the histories of political parties and electoral alliances do not resemble the "well"-structured party systems of Western Europe for whom the database was originally designed. Frequently changing electoral alliances, local electoral pacts or implosions of entire party systems (as in Italy in the mid-1990s) confront us with serious difficulties in identifying and coding political parties and their electoral performance on a continuous basis. As denoted above, these deviant cases are so multifaceted that they can hardly be captured by consistent error codings. For that reason no specific guideline is given in the codebook and every case needs to be commented by hand. The final datasets contain each of these commentaries so that also these "coding outliers" are made transparent to the end-user. Nevertheless, they are difficult to be integrated in the final analysis for the researcher since every single case has to be considered individually.

A second pain point refers to the history of the development of the database and the corresponding inter-coder reliability. Most often, the current coder (student assistant) does only know a limited number of his or her predecessors with the consequence that there is no guarantee that specific coding decisions (which cannot be directly derived from the codebook due to their rare appearance) are made consistently across coders. Hence, we are confronted with highly individualized knowledge concerning coding decisions on which we cannot be sure that they were transparently handed down to future coders. To put this simple, in spite of the existence of a extensive codebook we can give only limited information concerning the intercoder reliability of our project. For that reason, one specific task of the present is also to accurately check past codings in order to guarantee that the database includes the same information over time.

<font color="red">Words: 330/200-400</font>

# Key benefits
One central concern of our workflow is to make our procedure of data collection and processing transparent to the end-user. While a number of datasets on election results, government formations or electoral systems exists, none provides sufficient information to retrace the process of data coding back to the initial source. For that reason, we provide the end-user with a codebook that lists all regular coding decisions. As denoted above, data entries that do not follow these rules are coded and commented in a special way which can be assessed within the datasets that we provide. Moreover, we give the user the opportunity to also consider the original source we used to enter the data along with the corresponding coding decisions which are annotated on the source document. As mentioned in the introduction of this case study, there exist manifold ways to collect and aggregate data on political parties, elections and governments. Only if the researcher has perfect control and knowledge over the dataset and the corresponding decisions made during it creation, he or she can be sure that her or his analysis is not flawed by irregular or unexpected coding decisions. For that reason, we believe that our approach helps to ensure a high level of quality in the field of comparative politics.


<font color="red">Words: 213/200-400</font>


# Key tools

The core of our workflow is certainly the PostgreSQL-database, which allows us  to easily store a relational database. In contrast to the Microsoft Access database, which we use in order to provide an easily accessible user interface for the data entry, PostgreSQL is a object-relational database management system that comes with no charge. Due to its compatibility with other important software of our workflow, such as _Microsft Access_, _Git_ and _R_ (and with this _knitr_ and _Shiny_), it constitutes a flexible tool. Due to this, we can automatically produce periodic reports on changes in the dataset as well as  quickly identify failed consistency checks. This facilitates us to ensure a high quality of the data. Apart from these automated procedures, it enables us to access all versions of the database and the corresponding _R_-scripts via a version control system such as _git_. This allows the end-user to access any data version of the past so that past research results can be easily reproduced without dealing with updated versions of the datasets.

<font color="red">Words: 171/200-400</font>


# General questions about reproducibility

1. __Why do you think that reproducibility in your domain is important?__
  Political scientists learn from empirical experience. If
  contributions to our field are not transparent enough to be
  reproduced, then nothing can be learned from them. However,
  reproducibility covers both data generation and analysis.
  The Garbage-In-Garbage-Out principle applies to all studies
  that fail on either side of the equation.  
2. __How or where did you learn the reproducible practices described in your case study?__
  Some practices we use are common standard and should be
  taught in every introductory methods class. Others we learned
  from more tech savvy colleagues. Magic happened once we put
  the two together.
3. __What do you see as the major pitfalls to doing reproducible research in your domain, and do you have any suggestions for working around these? Examples could include legal, logistical, human, or technical challenges.__
  We see two major pitfalls. First, political
  scientists often receive strong training in qualitative or
  quantitative methods, but not in basic data management.
  For example, it is not unheard of that graduate students
  merge datasets row by row in Excel. Much would be gained
  if Political Science curricula would teach at least
  minimal data management skills. Second, our field rewards
  productivity, not thoroughness. We finish one project and
  quickly move on, leaving procedures of data generation and
  analysis poorly documented. To ensure at least a minimal
  level of reproducibility the provision of replication
  packages containing raw data, data management and analysis
  scripts should be made mandatory.
4. __What do you view as the major incentives for doing reproducible research?__
  Political scientists learn from experience. Reproducible
  research hence establishes a baseline against which to
  compare future analyses.
5. __Are there any broad reproducibility best practices that you'd recommend for researchers in your field?__
  Never change your raw data file. Stay away from the GUI.
  Have at least on notebook detailing the development of
  your analysis. Always comment your code or field notes.
6. __Would you recommend any specific websites, training courses, or books for learning more about reproducibility?__
