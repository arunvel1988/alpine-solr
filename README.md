[![build status](http://gitlab.tutum.ixishosting.co.uk/ci/projects/2/status.png?ref=master)](http://gitlab.tutum.ixishosting.co.uk/ci/projects/2?ref=master)

**This image is based off the official Solr image with modifications to work under Alpine Linux.**

***

# How to use this Docker image

To run a single Solr server:

    SOLR_CONTAINER=$(docker run -d -p 8983:8983 -t alpine-solr)

Then with a web browser go to `http://hostname:8983/` to see the Admin Console (adjust the hostname for your docker host).

To use Solr, you need to create a "core", an index for your data. For example:

    docker exec -it --user=solr $SOLR_CONTAINER bin/solr create_core -c gettingstarted

In the web UI if you click on "Core Admin" you should now see the "gettingstarted" core.

If you want to load some example data:

    docker exec -it --user=solr $SOLR_CONTAINER bin/post -c gettingstarted example/exampledocs/manufacturers.xml

In the UI, find the "Core selector" popup menu and select the "gettingstarted" core, then select the "Query"
menu item. This gives you a default search for "*:*" which returns all docs. Hit the "Execute Query" button,
and you should see a few docs with data. Congratulations!

To learn more about Solr, see the [Apache Solr Reference Guide](https://cwiki.apache.org/confluence/display/solr/Apache+Solr+Reference+Guide).
