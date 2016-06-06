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
database that includes more than seventy countries around
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

Our workflow {~~can be distinguished->has~~} {--into--} four
separate steps. {++Data first have to be hand coded. Second,
codings go through different human supervised and automated
consistency checks. Third, the newly generated data are
processed before storing them in our back-end database.
Finally, information can be outputted from our database. All
steps ++} {--which--} can be fulfilled independently of each
other. Apart from the single steps of the workflow, the
colored areas document the software and tools that is used
in each step. Our team consists of one student assistant,
two research fellows as well ons senior research fellow.
While the first is responsible for the coding and input of
the data as well as some basic consistency checks, automated
data tests as well as processing are maintained by our
research fellows. A codebook lists the majority of coding
decisions that are needed to enter the data correctly by our
research assistant.

In general, we are concerned with three basic challenges
while collecting, coding and processing our data: reduce
coding errors, maintain a high degree of intercoder
reliability and provide a transparent documentation of
coding decisions and data processing. The following
paragraphs will specifically focus on these challenges.

\textbf{Part I:}

{--As can be seen in the workflow diagram, t--}
The first decision to be made is whether a new observation
needs to be added to the dataset. For that purpose we
identify all upcoming elections and government formations
within our country sample of 70(???) countries in the world.
Once a new data entry is necessary, adequate sources have to
be identified by the coder in order to ensure the correct
documentation of party histories, election results and/or
government events.

Evaluating the quality of the source is essential for us
since only those election and government documents that
provide us with information as disaggregated as possible
guarantee that we can reliably and correctly code the
respective data. For that purpose, a list of high quality
sources is included in the codebook. If, due to lack of
reliable sources, information from non-identified sources
has been used, these data entries are flagged in order to
identify more reliable sources in the future. Once a source
has been identified, the data is coded manually following
the rules of the codebook.

\textbf{Part II:}

Based on this the data is entered into a Microsoft Access
Database and the source (including the coding decisions) is
saved on a server which can be assessed by all users of the
dataset. Although MS Access is not a free software, tool, it
provides a) a relational database that can be easily
maintained by research fellows and b) a user interface that
makes the data entry clear and easily understable even for
new coders. Hence, our student assistants can quickly
acquire the knowledge necessary to document the data with
the codebook, while the MS Access interface serves as a
\textcolor{red}{{++standardized++} coding structure} that
reduces error{--s--} and facilitates a high{--er--} degree
of intercoder reliability.

\textbf{Part III:}

Moreover, the MS Access interface allows to perform basic
consistency checks with the consequence that the coder can
easily evaluate the reliability of the used sources and its
information. As can be seen in the workflow diagram, if
these checks fail, new sources have to be considered in
order to reach an error-free documentation of the data.

After the data entry has been finalized by the coder, the
data is automatically \textcolor{red}{exported} to a
PostgreSQL-Database which allows us to store the dataset and
to put it under version control. {~~On a daily basis,
c->C~~}hanges {~~in->to~~} the dataset are documented {++on
a daily basis++}. At the same time, automated, more complex
consistency checks are performed by making use of the open
source statistic software
R.\footnote{https://www.r-project.org/.} Based on these, pdf
reports are created using the R-package
\textit{knitr}\footnote{\textit{knitr}
(http://yihui.name/knitr/) allows to create dynamic \LaTeX-
documents with R.} and send to one of our research
fellows/seniors(?). These include a documentation of all new
data entries, of all data changes as well as a list of
failed consistency checks. Due to this, the work of our
coder {~~is->can~~} easily {~~trackable->be tracked~~} by
experienced colleagues and possible coding errors
{~~can->are~~} easily {~~detected->spotted~~}.

Apart from performing consistency checks, the R-scripts also
process the data, i.e. {++they++} join different tables and
drop irrelevant variables, in order to provide a raw dataset
which includes basically all data entries without any
additional measures. After that, manual error coding is
conducted and documented if no high-quality source is
available or the correct coding of the data fails for some
other reasons (e.g. specific electoral systems). Based on
this raw dataset, further additional calculations are
conducted using R in order to provide an extended dataset
that includes additional common measures in the discipline
(such as the effective number of parties, the Gallagher
“Least Squares Index” or the Balance of powers Index).

\textbf{Part IV:}

After these steps are finished, the dataset is publicly
accessible via Shiny-Interface\footnote{Shiny is a web
application framework for R. See http://shiny.rstudio.com/.}
which allows the enduser (currently the members of our
research department) to browse and download the raw as well
as the aggregated dataset. In addition the aforementioned
codebook of the database can be downloaded in order to
guarantee a high transparency of coding decisions.

# Pain points

One pain point {--in our procedure of data collection and
processing --}is to manually code and document cases that do
not fit our pre-defined coding scheme. That is for instance
the case for our documentation of political parties and
their election results. In many countries, the histories of
political parties and electoral alliances do not resemble
the ``well''-structured party systems of Western Europe for
whom the database was originally designed. Frequently
changing electoral alliances, local electoral pacts or
implosions of entire party systems (as in Italy in the mid-
1990s) confront us with serious difficulties in identifying
and coding political parties and their electoral performance
on a continuous basis. Occasionally, coding decisions are
made in these cases that do not correspond to the codebook.
While all codings that differ from those provided in the
codebook are documented in a specified column of the dataset
and is, thus, easily accessible, this information is
difficult to integrate into analyses by the enduser.

A second pain point refers to the history of the development
of the database and the corresponding inter-coder
reliability. Most often, the current coder (student
assistant) does only know a limited number of his or her
predecessors with the consequence that there is no guarantee
that specific coding decisions (which cannot be directly
derived from the codebook due to their rare appearance) are
made consistently across coders. Hence, we are confronted
with {--a--} highly {~~hierarchized->individualized~~}
knowledge concerning coding decisions on which we cannot be
sure that they were transparently handed down to future
coders. As noted by \citet[141]{krippendorf_content_2000},
``without the establishment of reliability, content analysis
measures are useless.'' For that reason, one specific task
of the present is also to accurately check past codings in
order to guarantee that the database includes the same
information over time.

# Key benefits

One central concern of our workflow is to make our procedure
of data collection and processing transparent to the end-
user. While a number of datasets on election results,
government formations or electoral systems exists, none
provides sufficient information to retrace the process of
data coding back to the initial source. For that reason, we
provide the end-user with a codebook that lists all regular
coding decisions. If data entries do not follow these rules,
these "irregular" codings are commented in specific
\textcolor{red}{remark-fields} which can be assessed within
the datasets that we provide. Moreover, we give the user the
opportunity to also consider the original source used to
enter the data along with the corresponding coding decisions
which are annotated on the source document. As mentioned in
the introduction of this case study, there exist manifold
ways to collect and aggregate data on political parties,
elections and governments. Only if the researcher has
perfect control and knowledge over the dataset and the
corresponding decisions made during this process, he or she
can be sure that her or his analysis is not flawed by
irregular or unexpected coding decisions. For that reason,
we believe that our approach helps to ensure a high level of
quality in the research field of comparative politics.

# Key tools

The core of our workflow is certainly the
PostgreSQL-database, which allows us not only to easily
store a relational database on a
server.\footnote{https://www.postgresql.org/} In contrast to
the Microsoft Access database, which we use in order to
provide an easily accessible user interface for the data
entry, PostgreSQL is a free object-relational database
management system and comes with no charge. Due to its
excellent compatibility with other important software of our
workflow, such as Microsft Access and R (and with this knitr
and Shiny), it constitutes a flexible tool that also allows
us to version control our database. Moreover it gives us the
opportunity to automatically produce periodic reports on
changes in the dataset as well as to quickly identify failed
consistency checks. This facilitates us to ensure a high
quality of the data. Apart from these automated procedures,
it enables us to access all versions of the database either
via a version control system such as \textit{git}.
Furthermore, the version control allows the enduser to
access any data version of the past so that past research
results can be easily reproduced without dealing with
updates of the datatset.

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
