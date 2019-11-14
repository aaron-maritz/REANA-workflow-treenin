# REANA-workflow-treenin
Basic implementation for running on REANA cluster

Steps to succeed:

  First build docker image locally and run it. (accomplished prior)
  
  Run yadage script for initial step (see https://yadage.github.io/tutorial/GettingStarted.html).
  If it cannot handle loading in the test dataset, it will need to be passed in as a parameter.
  
  See where this outputs to, and in what format.
  Then run another yadage script for step 2, and step 3.
  
  Make these three steps into the steps.yml file (interpolated-cmd steps) See the different uses of publisher.
  
  At this point -> the entire analysis is done, it just needs to be tied together in a workflow.
  This is the .workflow part -> take the input from one, tie it into another etc...
  
  **** At this point local testing should still function, after this is REANA ****
  
 finish REANA.yaml file -> run using minikube. (Change server_url/access_token) See reana site for usage.
 $ # create new virtual environment
$ virtualenv ~/.virtualenvs/myreana
$ source ~/.virtualenvs/myreana/bin/activate
$ # install REANA client
$ pip install reana-client
$ # connect to some REANA cloud instance
$ export REANA_SERVER_URL=https://reana.cern.ch/
$ export REANA_ACCESS_TOKEN=XXXXXXX
$ # create new workflow
$ reana-client create -n my-analysis
$ export REANA_WORKON=my-analysis
$ # upload input code and data to the workspace
$ reana-client upload ./code ./data
$ # start computational workflow
$ reana-client start
$ # ... should be finished in about a minute
$ reana-client status
$ # list workspace files
$ reana-client list
$ # download output results
$ reana-client download results/plot.png
