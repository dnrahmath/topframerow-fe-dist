# Git settings
BRANCH_PRODUCTION := master
BRANCH_STAGING := develop

# Git operations
pull-production:
	git pull origin $(BRANCH_PRODUCTION) --no-ff

pull-staging:
	git pull origin $(BRANCH_STAGING) --no-ff

# Force pull
force-pull-production:
	git fetch origin
	git reset --hard origin/$(BRANCH_PRODUCTION)
	git clean -fd

force-pull-staging:
	git fetch origin
	git reset --hard origin/$(BRANCH_STAGING)
	git clean -fd

# File permissions
give-access-production:
	chown -R $(USER):web /var/www/production/topframerow-fe-dist
	chmod -R u+rw /var/www/production/topframerow-fe-dist

give-access-staging:
	chown -R $(USER):web /var/www/staging/topframerow-fe-dist
	chmod -R u+rw /var/www/staging/topframerow-fe-dist