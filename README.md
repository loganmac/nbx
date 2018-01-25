# nbx


## Examples
----- Running a dev|live box

nbx dev|live run [-e env]               # Start the cluster.
nbx dev|live run [-e env] web.main      # Attach to a running container within the cluster, and drop into bash.
nbx dev|live run [-e env] web.main cmd  # Attach to a running container within the cluster, and exec a command inside, then return once complete.
nbx dev|live stop                       # Stop the cluster.
nbx dev|live logs                       # Stream the cluster logs.
nbx dev|live info                       # Show IP/alias/evar/secrets/status/containers/bridge info for the cluster.
nbx dev|live destroy                    # Destroy the containers and volumes associated with an environment.


### start the cluster
nbx dev run

### run one-off commands within the cluster, on the web.main container
nbx dev run web.main rake -T
nbx dev run web.main rails c

----- Emulate a live app

### emulate the production stack
nbx live -e prod

### Run the postgres client inside of the data.db container (run some queries)
nbx live run data.db pg

----- Global / Platform commands

nbx init      # Initialize a .nbx.yml file and a .nbx.secrets.yml for a project.
nbx setup     # Install/configure platform, docker, bridge, db, etc.
nbx start     # Starting the platform, docker, bridge.
nbx stop      # Stop all clusters, the platform, bridge, etc.
nbx info      # Show the status of the platform, docker, bridge, clusters, etc.
nbx implode   # Delete nbx and all configuration.
nbx login     # Login to a nanobox account.
nbx logout    # Logout of a nanobox account.

----- Image / Registry management

nbx registry  add|rm|ls                   # Add, remove, and list docker registry endpoints.
nbx push      [registry] [env] [--debug]  # Build and push the built images to the docker registry.

----- Nanobox / Remote app management

nbx deploy [remote]                    # Deploy the recently pushed images and nbx config to a live app.

nbx remote          add|rm|ls          # Add, remove, and list nanobox live remote apps.
nbx remote [remote] logs               # Fetch/stream logs from a production app.
nbx remote [remote] console            # Console into a live app server or container.
nbx remote [remote] tunnel data.db     # Establish a tunnel into a live app database.
nbx remote [remote] secret add|rm|ls   # Add/rm/ls remote secrets.


Hurdles:
  Log
  DB (key/val)
  Global Config
  Boxfile parsing
  Output (sanitizing/summarizing/animation)
