#!/usr/bin/env groovy

/**
	# Pull Requests
		- Build specific configuration for that branch (main -> dev, alpha -> alpha)

	# Branches (ex: main or alpha)
		- Build specific configuration for that branch (main -> dev, alpha -> alpha)
		- Deploys to specific environment for that branch (main -> dev, alpha -> alpha)
*/


pipeline {
	agent {
		label "macos-test"
	}

	options {
		ansiColor('xterm')
		disableConcurrentBuilds(abortPrevious: true)
		skipStagesAfterUnstable()
	}

	stages {
		stage('Run') {
			steps {
				fastlane("foo")
			}
		}
	}
}

def fastlane(lane) {
	sh """#!/bin/zsh -l
		asdf install
		corepack enable
		npm install --global zx
		npm install --global yarn
		asdf reshim nodejs
		bundle install

		bundle exec fastlane ${lane}
	"""
}
