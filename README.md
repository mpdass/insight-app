# insight-app
Insight Systems Puzzle with the bugs fixed as follows:
Changes made to the puzzle.
  1. Modified port mapping for 'nginx' from 80:8080 to 8080:80 (to match with the 'host:container' port format) - 'docker-compose.yml'
  2. Commented out 'EXPOSE 5001' in Docker file as this is not needed - 'Dockerfile'
  3. Updated 'proxy_pass' port from 5001 to 5000 which appeared to be the default port where 'flaskapp' was listening on internally.
  4. Commented out double 'proxy_set_header' in the 'conf.d/flaskapp.conf' that was causing incorrect return url with additional
        'localhost/ip' (where the request is originating from) with the redirect(url_for('success')) - 3,4 - 'conf.d/flaskapp.conf'
  5. The success url doesn't display added item names. This is either code in-complete/incorrect sql query. Not sure at this point
        if this is an issue to be resolved by me. However, updated 'success()' function in 'app.py' to list the items added.
  6. Sold item is not getting removed from the db entry. Additional coding for it. Not considering it as a bug, but treating it as a feature incomplete. - 5,6 - 'app.py'
