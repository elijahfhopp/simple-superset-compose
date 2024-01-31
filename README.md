# simple-superset-compose

This is a minimal [Superset](https://superset.apache.org/) + Docker Compose set up. It's intended to simplify the process of trying out Superset.

:warning: **simple-superset-compose is not intended for production use. There are unsafe settings enabled in `superset/superset_config.py`.**

## Usage

1. Determine if you need to make any changes to `superset_config.py` (more info [here](https://superset.apache.org/docs/installation/configuring-superset)). If you ever make any changes to `superset_config.py`, make sure to rebuild the docker images (`docker compose build`).

2. Run `docker compose up`. If it is logging errors about creating a database, the permissions of the new `superset_home` folder may be too restrictive (i.e. `chmod 777 superset_home`).

3. Run the `setup.sh` file, which initializes an account named `admin` with the password `secret`.

4. Visit [http://localhost:8080](http://localhost:8080).

5. [Connect the running PostgreSQL to Superset](https://superset.apache.org/docs/databases/db-connection-ui). The settings will be:
   
| HOST | PORT | DATABASE NAME | USERNAME | PASSWORD |
|---|---|---|---|---|
| database| 5432 | superset | superset | secretsecret |

6. Insert data into the database via the exposed port (`5000` by default), or [via the Superset UI](https://superset.apache.org/docs/creating-charts-dashboards/exploring-data/).

7. Try Superset.

8. Profit!

## Notes

Apache Superset comes with a default Docker Compose setup, but it is not very condusive to trying out the basic functionality of Superset in your local env. This little compose file is the (impercise, quick-n-dirty) product of me wanting to trying out Superset, but shying away from the intensive setup process. It's simple nature lends itself well to use as a little offline anylitics app/SQL exploration lab with fancy graphs/a workspace to safely try out Superset development. Enjoy!
