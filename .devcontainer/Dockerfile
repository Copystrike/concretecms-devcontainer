FROM ghcr.io/concrete5-community/docker5:base

ENV CCM_PHP_VERSION=8.1
ENV CCM_COMPOSER_VERSION=2
ENV CCM_PHPUNIT_VERSION=8
ENV CCM_C5_ARCHIVE=https://github.com/concretecms/concretecms/archive/master.tar.gz
ENV CCM_STARTING_POINT=atomik_full
ENV CCM_PATCH_ENVIRONMENT_ONLY=N

COPY assets/nginx.conf /etc/nginx/sites-available/default
COPY assets/app-patch /tmp/
COPY assets/start-patch /tmp/
