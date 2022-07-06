FROM apache/superset

# settting args
ARG SUPERSET_ADMIN_USERNAME="admin"
ARG SUPERSET_ADMIN_FIRSTNAME="Superset"
ARG SUPERSET_ADMIN_LASTNAME="Admin"
ARG SUPERSET_ADMIN_EMAIL="admin@superset.com"
ARG SUPERSET_ADMIN_PASSWORD="admin"

# Switching to root to install the required packages
USER root

# Switching back to using the `superset` user
USER superset

# Setup local admin account
RUN superset fab create-admin \
  --username ${SUPERSET_ADMIN_USERNAME} \
  --firstname ${SUPERSET_ADMIN_FIRSTNAME} \
  --lastname ${SUPERSET_ADMIN_LASTNAME} \
  --email ${SUPERSET_ADMIN_EMAIL} \
  --password ${SUPERSET_ADMIN_PASSWORD}

# Migrate local DB to latest
RUN superset db upgrade

# Load Examples
RUN superset load_examples

# Setup roles
RUN superset init