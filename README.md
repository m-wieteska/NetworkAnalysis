# NetworkAnalysis
# Project Description: use network analysis capabilities in R to understand/ discover how originally defined group of subject matter experts (SMEs) is performing. For that purpose gathered were two datasets: 1st) 1 month after the group was set up, 2nd) 4 months from the set up date. Data represents emails echange streams within SME groups and between indivuduals external to the SMEs group. Data visualization (network) waas used to present changes that happened to the originally defined group. 

# Data use: there will be two data sets to compare

* status in progress *
* second data set collected

# R code # 
próbowanie adresu URL 'https://cran.rstudio.com/bin/windows/contrib/3.6/ape_5.3.zip'
Content type 'application/zip' length 2835415 bytes (2.7 MB)
downloaded 2.7 MB

package ‘ape’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Users\Michal\AppData\Local\Temp\RtmpuUQiGW\downloaded_packages
> library(ape)

Dołączanie pakietu: ‘ape’

Następujące obiekty zostały zakryte z ‘package:igraph’:

    edges, mst, ring

Komunikat ostrzegawczy:
pakiet ‘ape’ został zbudowany w wersji R 3.6.3 
> plot(as.phylo(SMEnetwork), type = "fan")
Błąd w poleceniu 'UseMethod("as.phylo")':
  niestosowalna metoda dla 'as.phylo' zastosowana do obiektu klasy "igraph"
> plot(as.phylo(SMEnetwork), cex = 0.6, label.offset = 0.5)
Błąd w poleceniu 'UseMethod("as.phylo")':
  niestosowalna metoda dla 'as.phylo' zastosowana do obiektu klasy "igraph"
> plot(as.phylo(SMEnetwork), type = "fan")
Błąd w poleceniu 'UseMethod("as.phylo")':
  niestosowalna metoda dla 'as.phylo' zastosowana do obiektu klasy "igraph"
> SMEnetw <- read.csv(file.choose(), header = T, sep = ";", fileEncoding="UTF-8-BOM")
> str(SMEnetw)
'data.frame':	264 obs. of  3 variables:
 $ SMEstart        : Factor w/ 16 levels "A","B","C","D",..: 1 13 4 6 5 12 7 15 2 10 ...
 $ SMEend          : Factor w/ 18 levels "A","B","D","E",..: 18 2 11 17 7 18 2 11 17 7 ...
 $ ContactFrequency: int  4 2 5 7 8 5 3 5 7 8 ...
> #fix(SMEnetw)
> SME_analysis <- data.frame(SMEnetw$SMEstart, SMEnetw$SMEend, SMEnetw$ContactFrequency)
> SMEnetwork <- graph.data.frame(SME_analysis, directed = T)
> plot(as.phylo(SMEnetwork), type = "fan")
Błąd w poleceniu 'UseMethod("as.phylo")':
  niestosowalna metoda dla 'as.phylo' zastosowana do obiektu klasy "igraph"
> as.phylo(SMEnetwork)
Błąd w poleceniu 'UseMethod("as.phylo")':
  niestosowalna metoda dla 'as.phylo' zastosowana do obiektu klasy "igraph"
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> ?as.phylo
> SMEnetwork <- as.phylo(SMEnetwork)
Błąd w poleceniu 'UseMethod("as.phylo")':
  niestosowalna metoda dla 'as.phylo' zastosowana do obiektu klasy "igraph"
> tree <- rtree(n = 20)
> plot(tree, edge.width = 2)
> tree <- rtree(SMEnetwork)
Błąd w poleceniu 'rtree(SMEnetwork)':
  'list' object cannot be coerced to type 'integer'
> plot(tree, edge.width = 2)
> tree <- rtree(n = 110)
> plot(tree, edge.width = 2)
> tree <- rtree(n = SMEnetwork)
Błąd w poleceniu 'rtree(n = SMEnetwork)':
  'list' object cannot be coerced to type 'integer'
> plot(tree, edge.width = 2)
> tree <- rtree(SMEnetwork$SMEStart)
Błąd w poleceniu 'if (n < 2) stop("a tree must have at least 2 tips.")':
  argument jest długości zero
> plot(tree, edge.width = 2)
> tree <- rtree(n = 12)
> plot(tree, edge.width = 2)
> tree <- read.tree(text = "(((A,B),(C,D)),E);")
> plot(tree, type = "cladogram", edge.width = 2)
> tree <- read.tree(SMEnetwork)
Błąd w poleceniu 'scan(file = file, what = "", sep = "\n", quiet = TRUE, skip = skip, ':
  'file' must be a character string or connection
> plot(tree, type = "cladogram", edge.width = 2)
> tree <- read.tree(SMEnetwork)
Błąd w poleceniu 'scan(file = file, what = "", sep = "\n", quiet = TRUE, skip = skip, ':
  'file' must be a character string or connection
> plot(tree, type = "cladogram", edge.width = 2)
> tree <- read.tree(SMEnetwork)
Błąd w poleceniu 'scan(file = file, what = "", sep = "\n", quiet = TRUE, skip = skip, ':
  'file' must be a character string or connection
> plot(tree, type = "cladogram", edge.width = 2)
> tree <- read.tree(SMEnetwork)
Błąd w poleceniu 'scan(file = file, what = "", sep = "\n", quiet = TRUE, skip = skip, ':
  'file' must be a character string or connection
> plot(tree, type = "cladogram", edge.width = 2)
> tree <- read.tree(SMEnetwork$SMEStart)
Błąd w poleceniu 'scan(file = file, what = "", sep = "\n", quiet = TRUE, skip = skip, ':
  'file' must be a character string or connection
> plot(tree, type = "cladogram", edge.width = 2)
> tree <- read.tree(SMEnetwork$SMEStart)
Błąd w poleceniu 'scan(file = file, what = "", sep = "\n", quiet = TRUE, skip = skip, ':
  'file' must be a character string or connection
> plot(tree, type = "cladogram", edge.width = 2)
> tree <- read.tree(text = "(((A,B),(C,D,E)),F);")
> plot(tree, type = "cladogram", edge.width = 2)
> tree <- read.tree(SMEnetwork$SMEStart)
Błąd w poleceniu 'scan(file = file, what = "", sep = "\n", quiet = TRUE, skip = skip, ':
  'file' must be a character string or connection
> pdf.options(encoding='ISOLatin2')
> ls()
[1] "ceb"          "col.tr"       "palf"         "SME_analysis" "SMEnetw"      "SMEnetwork"  
[7] "tr"           "tree"        
> rm(list = ls())
> SMEnetw <- read.csv(file.choose(), header = T, sep = ";", fileEncoding="UTF-8-BOM")
> str(SMEnetw)
'data.frame':	264 obs. of  3 variables:
 $ SMEstart        : Factor w/ 16 levels "A","B","C","D",..: 1 13 4 6 5 12 7 15 2 10 ...
 $ SMEend          : Factor w/ 18 levels "A","B","D","E",..: 18 2 11 17 7 18 2 11 17 7 ...
 $ ContactFrequency: int  4 2 5 7 8 5 3 5 7 8 ...
> #fix(SMEnetw)
> SME_analysis <- data.frame(SMEnetw$SMEstart, SMEnetw$SMEend, SMEnetw$ContactFrequency)
> SMEnetwork <- graph.data.frame(SME_analysis, directed = T)
> V(SMEnetwork)$ContactFrequency <- degree(SMEnetwork)
> hist(V(SMEnetwork)$ContactFrequency, breaks = 25, prob = T,
+      col = 'dark blue',
+      main = 'Connections distribution',
+      ylab = 'Frequency',
+      xlab = 'Number')
> set.seed(85)
> plot(SMEnetwork)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.5,
+      layout=layout.fruchterman.reingold)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.5,
+      layout=layout.fruchterman.reingold)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.kamada.kawai)
> # next basic view
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.sphere)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.sphere)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.sphere)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.circle)
> plot(SMEnetwork,
+      vertex.color = rainbow(56),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.star)
> par(mfrow=c(2,2))
> par(mar=c(0.25,0.25,0.1,0.1))
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.graphopt)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter2",
+      font.main=1,
+      layout=layout.kamada.kawai)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter3",
+      font.main=1,
+      layout=layout.sphere)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter4",
+      font.main=1,
+      #xlab = 'iter4',
+      layout=layout.circle)
> par(bg="white") # set background
> 
> ceb <- cluster_edge_betweenness(SMEnetwork) 
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
> par(bg="white") # set background
> abline(v = xpoints, col = "grey90", lwd = 80)
Błąd w poleceniu 'int_abline(a = a, b = b, h = h, v = v, untf = untf, ...)':
  nie znaleziono obiektu 'xpoints'
> par(bg="lightblue") # set background
> 
> ceb <- cluster_edge_betweenness(SMEnetwork) 
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
> tree <- read.tree(text = "(((A,B),(C,D,E)),F);")
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> plot(cnet,
+      SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.kamada.kawai)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.color = rainbow(53), vertex.size = V(SMEnetwork)$ContactFrequency * ':
  nie znaleziono obiektu 'cnet'
> pdf.options(encoding='ISOLatin2')
> ls()
[1] "ceb"          "SME_analysis" "SMEnetw"      "SMEnetwork"   "tree"        
> rm(list = ls())
> SMEnetw <- read.csv(file.choose(), header = T, sep = ";", fileEncoding="UTF-8-BOM")
> str(SMEnetw)
'data.frame':	264 obs. of  3 variables:
 $ SMEstart        : Factor w/ 16 levels "A","B","C","D",..: 1 13 4 6 5 12 7 15 2 10 ...
 $ SMEend          : Factor w/ 18 levels "A","B","D","E",..: 18 2 11 17 7 18 2 11 17 7 ...
 $ ContactFrequency: int  4 2 5 7 8 5 3 5 7 8 ...
> #fix(SMEnetw)
> SME_analysis <- data.frame(SMEnetw$SMEstart, SMEnetw$SMEend, SMEnetw$ContactFrequency)
> SMEnetwork <- graph.data.frame(SME_analysis, directed = T)
> V(SMEnetwork)$ContactFrequency <- degree(SMEnetwork)
> hist(V(SMEnetwork)$ContactFrequency, breaks = 25, prob = T,
+      col = 'dark blue',
+      main = 'Connections distribution',
+      ylab = 'Frequency',
+      xlab = 'Number')
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.5,
+      layout=layout.fruchterman.reingold)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.kamada.kawai)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.sphere)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.circle)
> plot(SMEnetwork,
+      vertex.color = rainbow(56),
+      # vertex.size = V(SMEnetwork)$degree*0.4,
+      edge.arrow.size = 0.1,
+      layout=layout.star)
> par(mfrow=c(2,2))
> par(mar=c(0.25,0.25,0.1,0.1))
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.graphopt)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter2",
+      font.main=1,
+      layout=layout.kamada.kawai)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter3",
+      font.main=1,
+      layout=layout.sphere)
> plot(SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter4",
+      font.main=1,
+      #xlab = 'iter4',
+      layout=layout.circle)
> par(bg="lightblue") # set background
> 
> ceb <- cluster_edge_betweenness(SMEnetwork) 
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> library(multinet)
Ładowanie wymaganego pakietu: Rcpp
Ładowanie wymaganego pakietu: RColorBrewer
Komunikaty ostrzegawcze:
1: pakiet ‘multinet’ został zbudowany w wersji R 3.6.3 
2: pakiet ‘Rcpp’ został zbudowany w wersji R 3.6.3 
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> layout_multiforce_ml(SMEnetwork, w_in = 1, w_inter = 1, gravity = 0, iterations = 100)
Błąd w poleceniu 'layout_multiforce_ml(SMEnetwork, w_in = 1, w_inter = 1, gravity = 0, ':
  Cannot convert object to an environment: [type=list; target=ENVSXP].
> layout_circular_ml(SMEnetwork)
Błąd w poleceniu 'layout_circular_ml(SMEnetwork)':
  Cannot convert object to an environment: [type=list; target=ENVSXP].
> plot(SMEnetwork)
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> par(bg="lightblue") # set background
> 
> ceb <- cluster_edge_betweenness(SMEnetwork) 
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> plot(SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
Błąd w poleceniu 'plot(cnet, SMEnetwork, vertex.size = 13, vertex.label.cex = 0.9, ':
  nie znaleziono obiektu 'cnet'
> SMEnetwork <- graph.data.frame(y, directed = F)
Błąd w poleceniu 'as.data.frame(d)':nie znaleziono obiektu 'y'
> cnet <- cluster_edge_betweenness(SMEnetwork)
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> 
> SMEnetwork <- graph.data.frame(y, directed = F)
Błąd w poleceniu 'as.data.frame(d)':nie znaleziono obiektu 'y'
> 
> SMEnetwork <- graph.data.frame(y, directed = F)
Błąd w poleceniu 'as.data.frame(d)':nie znaleziono obiektu 'y'
> SMEnetwork <- graph.data.frame(y, directed = F)
Błąd w poleceniu 'as.data.frame(d)':nie znaleziono obiektu 'y'
> cnet <- cluster_edge_betweenness(SMEnetwork)
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> SMEnetwork <- graph.data.frame(SMEnetwor, directed = F)
Błąd w poleceniu 'as.data.frame(d)':nie znaleziono obiektu 'SMEnetwor'
> cnet <- cluster_edge_betweenness(SMEnetwork)
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> SMEnetwork <- graph.data.frame(SMEnetwork, directed = F)
Błąd w poleceniu 'as.data.frame.default(d)':
  cannot coerce class ‘"igraph"’ to a data.frame
> cnet <- cluster_edge_betweenness(SMEnetwork)
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> 
> SMEnetwork <- graph.data.frame(SMEnetwork, directed = F)
Błąd w poleceniu 'as.data.frame.default(d)':
  cannot coerce class ‘"igraph"’ to a data.frame
> 
> SMEnetwork <- graph.data.frame(y, directed = F)
Błąd w poleceniu 'as.data.frame(d)':nie znaleziono obiektu 'y'
> 
> SMEnetwork <- graph.data.frame(SMEnetwork, directed = F)
Błąd w poleceniu 'as.data.frame.default(d)':
  cannot coerce class ‘"igraph"’ to a data.frame
> SMEnetwork1 <- graph.data.frame(SMEnetwork, directed = F)
Błąd w poleceniu 'as.data.frame.default(d)':
  cannot coerce class ‘"igraph"’ to a data.frame
> graph.data.frame(SMEnetwork, directed = F)
Błąd w poleceniu 'as.data.frame.default(d)':
  cannot coerce class ‘"igraph"’ to a data.frame
> SMEnetwor1 <- igraph::as_data_frame(SMEnetwor) 
Błąd w poleceniu '"igraph" %in% class(graph)':nie znaleziono obiektu 'SMEnetwor'
> SMEnetwor1 <- igraph::as_data_frame(SMEnetwork) 
> cnet <- cluster_edge_betweenness(SMEnetwork1)
Błąd w poleceniu '"igraph" %in% class(graph)':
  nie znaleziono obiektu 'SMEnetwork1'
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork)
> cnet <- cluster_edge_betweenness(SMEnetwork1)
Błąd w poleceniu 'cluster_edge_betweenness(SMEnetwork1)':Not a graph object!
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork1)
Błąd w poleceniu 'cluster_edge_betweenness(SMEnetwork1)':Not a graph object!
> plot(cnet,
+      SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.kamada.kawai)
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork2)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.kamada.kawai)
brak argument�w w max; zwracanie warto�ci -InfBłąd w poleceniu 'plot.window(...)':'xlim' potrzebuje skończonych wartości
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.kamada.kawai)
> 
> SMEnetwork <- graph.data.frame(SMEnetwork, directed = F)
Błąd w poleceniu 'as.data.frame.default(d)':
  cannot coerce class ‘"igraph"’ to a data.frame
> 
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> SMEnetwork <- graph.data.frame(SMEnetwork, directed = F)
Błąd w poleceniu 'as.data.frame.default(d)':
  cannot coerce class ‘"igraph"’ to a data.frame
> 
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> 
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork2)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork2)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.kamada.kawai)
brak argument�w w max; zwracanie warto�ci -InfBłąd w poleceniu 'plot.window(...)':'xlim' potrzebuje skończonych wartości
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork1)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.kamada.kawai)
Błąd w poleceniu 'V(SMEnetwork1)':Not a graph object
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork2)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.kamada.kawai)
brak argument�w w max; zwracanie warto�ci -InfBłąd w poleceniu 'plot.window(...)':'xlim' potrzebuje skończonych wartości
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.color = rainbow(53),
+      vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
+      edge.arrow.size = 0.1,
+      main="Iter1",
+      font.main=1,
+      layout=layout.kamada.kawai)
> par(mfrow=c(2,2))
> 
> par(bg="lightblue") # set background
> 
> ceb <- cluster_edge_betweenness(SMEnetwork) 
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
> 
> 
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork2)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> 
> par(mfrow=c(2,2))
> par(mar=c(0.25,0.25,0.1,0.1))
> 
> par(bg="lightblue") # set background
> 
> ceb <- cluster_edge_betweenness(SMEnetwork) 
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
> 
> 
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork2)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> 
> par(mfrow=c(2,1))
> par(mar=c(0.25,0.25,0.1,0.1))
> 
> par(bg="lightblue") # set background
> 
> ceb <- cluster_edge_betweenness(SMEnetwork) 
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
> 
> 
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork2)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> 
> par(mfrow=c(2,1))
> par(mar=c(0.25,0.1))
Błąd w poleceniu 'par(mar = c(0.25, 0.1))':
  parametr graficzny 'mar' posiada niepoprawną długość
> par(mfrow=c(2,1))
> par(mar=c(0.25,1.0))
Błąd w poleceniu 'par(mar = c(0.25, 1))':
  parametr graficzny 'mar' posiada niepoprawną długość
> par(mfrow=c(2,1))
> par(mar=c(0.25,0.75))
Błąd w poleceniu 'par(mar = c(0.25, 0.75))':
  parametr graficzny 'mar' posiada niepoprawną długość
> par(mfrow=c(2,1))
> par(mar=c(0.25,0.5))
Błąd w poleceniu 'par(mar = c(0.25, 0.5))':
  parametr graficzny 'mar' posiada niepoprawną długość
> par(mfrow=c(2,1))
> par(mar=c(0.25,0.25))
Błąd w poleceniu 'par(mar = c(0.25, 0.25))':
  parametr graficzny 'mar' posiada niepoprawną długość
> par(mfrow=c(2,1))
> par(mar=c(0.25,0.25,0.5,0.5))
> 
> par(bg="lightblue") # set background
> 
> ceb <- cluster_edge_betweenness(SMEnetwork) 
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
> 
> 
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork2)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> 
> par(mfrow=c(2,1))
> par(mar=c(0.15,0.15,0.5,0.5))
> 
> par(bg="lightblue") # set background
> 
> ceb <- cluster_edge_betweenness(SMEnetwork) 
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
> dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
> 
> 
> 
> SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
> SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
> cnet <- cluster_edge_betweenness(SMEnetwork2)
> 
> plot(cnet,
+      SMEnetwork,
+      vertex.size = 13,
+      vertex.label.cex = 0.9,
+      edge.arrow.size=0.1,
+      vertex.size = V(SMEnetwork2)$ContactFrequency*0.2,
+      layout=layout.graphopt)
> 
> 





Show in New WindowClear OutputExpand/Collapse Output
[1] "ceb"          "SME_analysis" "SMEnetw"      "SMEnetwork"   "tree"        
Show in New WindowClear OutputExpand/Collapse Output
'data.frame':	264 obs. of  3 variables:
 $ SMEstart        : Factor w/ 16 levels "A","B","C","D",..: 1 13 4 6 5 12 7 15 2 10 ...
 $ SMEend          : Factor w/ 18 levels "A","B","D","E",..: 18 2 11 17 7 18 2 11 17 7 ...
 $ ContactFrequency: int  4 2 5 7 8 5 3 5 7 8 ...
Show in New WindowClear OutputExpand/Collapse Output

Show in New WindowClear OutputExpand/Collapse Output

Show in New WindowClear OutputExpand/Collapse Output

Show in New WindowClear OutputExpand/Collapse Output

Show in New WindowClear OutputExpand/Collapse Output

Show in New WindowClear OutputExpand/Collapse Output

Show in New WindowClear OutputExpand/Collapse Output

Show in New WindowClear OutputExpand/Collapse Output

Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
R Console

Show in New WindowClear OutputExpand/Collapse Output

Show in New WindowClear OutputExpand/Collapse Output

Show in New WindowClear OutputExpand/Collapse Output

Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
Modularity is implemented for undirected graphs only.
R Console
