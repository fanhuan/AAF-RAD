**AAF-RAD**
===========

A program to simulate raw RADseq-like data with options to modify tree, population, sequencing, and formatting parameters. 

Requirements
------------
+ Python 2.7+
+ Numpy Python module
+ `Egglib Python module <http://mycor.nancy.inra.fr/egglib/>`_

Installation:
-------------
1. Install the `Egglib Python module <http://egglib.sourceforge.net/>`_ v.2 (not v.3) `(I recommend these install instructions) <http://wjidea.github.io/2016/installEgglib.html>`_
2. Download or clone *simrrls*.  
3. 'cd' into the top-level `simrrls/` directory that contains the file setup.py
4. run 'pip install .'  or 'python setup.py install'

Example usage: 
---------------

See all parameter options:

.. code:: bash  

    $ simrrls -h
    
    optional arguments:
    -h, --help      show this help message and exit
    --version       show program's version number and exit
    -o outname      [str] output file name prefix (default 'out')
    -mc dropout     [0/1] allelic dropout from mutation to cut sites (default 0)
    -ms dropout     [0/1] allelic dropout from new cut sites in seq (default 0)
    -e error        [float] sequencing error rate (default 0.0005)
    -f datatype     [str] datatype (default rad) (options: rad, gbs, ddrad,
                    pairddrad, pairgbs)
    -I indels       [float] rate of indel mutations (default 0) ex: 0.001
    -l length       [int] length of simulated sequences (default 100)
    -L nLoci        [int] number of loci to simulate (default 100)
    -n Ninds        [int] N individuals from each taxon (default 1)
    -N Ne           [int] pop size (Ne for all lineages; default 5e5)
    -t tree         [str] file name or newick string of ultrametric tree
                    (default 12 taxon balanced tree w/ bls=1)
    -u mu           [float] per site mutation rate (default 1e-9)
    -df depthfunc   [str] model for sampling copies (default norm, other=exp)
    -dm depthmean   [int] mean sampled copies in norm, 1/m for exp (default 10)
    -ds depthstd    [int] stdev sampled copies, used with norm model (default 0)
    -c1 cut_1       [str] restriction site 1 (default CTGCAG)
    -c2 cut_2       [str] restriction site 1 (default CCGG)
    -i1 min_insert  [int] total frag len = (2*l)+insert (default 100)
    -i2 max_insert  [int] total frag len = (2*l)+insert (default 400)
    -r1 seed_1      [int] random seed 1 (default 1234567)
    -r2 seed_2      [int] random seed 2 (default 7654321)


Modified population parameters::

    $ simrrls -o test2 -N 1e6 -u 2e-8 

Modified sequencing parameters::

    $ simrrls -o test3 -L 5000 -l 200 -e 0.001 -dm 10 -ds 2 

Modified library type (In this case allowing paired-end reads overlap)::

    $ simrrls -o test4 -f pairddrad -i1 -50 -i2 200 

Modified topology:

.. code:: bash  

    $ echo "((a:1,b:1):1,c:2);" > treefile  
    $ simrrls -o test5 -t treefile  





0
