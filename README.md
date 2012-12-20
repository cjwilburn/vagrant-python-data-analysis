vagrant-python-data-analysis
============================

What
====
Vagrant/Chef files for a data analysis python environment. 

* Basebox = precise64
* Creates a Python virtual environment (*pythondata* by default)
* Installs data analysis-related Python packages and their dependencies
* Includes packages required for [IPython Notebook](http://ipython.org/ipython-doc/dev/interactive/htmlnotebook.html) server

How
===
1. Install [vagrant](http://vagrantup.com/)
2. Download and Install [VirtualBox](http://www.virtualbox.org/)
3. Clone this repo
4. Go to the repo and launch the box

        cd [repo]
        vagrant up
5. To run a public IPython Notebook server that's accessible from the host machine's browser:
    1. Follow _Running a public notebook server_ directions [here](http://ipython.org/ipython-doc/dev/interactive/htmlnotebook.html).
    2. The sample config in the above directions uses port 9999. By default, this project forwards VM port 9999 to 9998. Therefore, you can access IPython notebooks from your host at [http://127.0.0.1:9998](http://127.0.0.1:9998).
