# Test case for npm issue #3241

This is a test case for an [npm issue][1] where an `npm install` hangs if there is a tarball in the dependencies of a package.

To repeat the bug run

    npm install

You will see that the install hangs after npm reports that the packages have been installed. The process exits ok after that. 

This bug report is repeatable on 

* OSX 10.8.2
* Node 0.10.0
* npm 1.2.14

Debug information from `npm -d install`.

    npm info it worked if it ends with ok
    npm info using npm@1.2.14
    npm info using node@v0.10.0
    npm info preinstall npm-3241-testcase@0.0.0
    npm info trying registry request attempt 1 at 07:01:32
    npm http GET https://registry.npmjs.org/grunt-contrib-jshint/0.2.0
    npm http 304 https://registry.npmjs.org/grunt-contrib-jshint/0.2.0
    npm info install grunt-contrib-jshint@0.2.0 into /Users/george/code/npm-3241-testcase
    npm info installOne grunt-contrib-jshint@0.2.0
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint unbuild
    npm info preinstall grunt-contrib-jshint@0.2.0
    npm info trying registry request attempt 1 at 07:01:33
    npm http GET https://registry.npmjs.org/jshint
    npm http 304 https://registry.npmjs.org/jshint
    npm info install jshint@1.0.0 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint
    npm info installOne jshint@1.0.0
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint unbuild
    npm info preinstall jshint@1.0.0
    npm info retry fetch attempt 1 at 07:01:35
    npm info trying registry request attempt 1 at 07:01:35
    npm http GET https://registry.npmjs.org/shelljs
    npm info trying registry request attempt 1 at 07:01:35
    npm http GET https://registry.npmjs.org/underscore
    npm http GET https://github.com/ariya/esprima/tarball/master
    npm info trying registry request attempt 1 at 07:01:35
    npm http GET https://registry.npmjs.org/peakle
    npm info trying registry request attempt 1 at 07:01:35
    npm http GET https://registry.npmjs.org/cli/0.4.3
    npm info trying registry request attempt 1 at 07:01:35
    npm http GET https://registry.npmjs.org/minimatch
    npm http 304 https://registry.npmjs.org/cli/0.4.3
    npm http 304 https://registry.npmjs.org/underscore
    npm http 304 https://registry.npmjs.org/shelljs
    npm http 304 https://registry.npmjs.org/peakle
    npm http 304 https://registry.npmjs.org/minimatch
    npm http 200 https://github.com/ariya/esprima/tarball/master
    npm info shasum 6538a2f744a336f8d25a12a512075335b4c80746
    npm info shasum /Users/george/.npm/esprima/1.1.0-dev/package.tgz
    npm info install cli@0.4.3 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint
    npm info install underscore@1.4.4 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint
    npm info install shelljs@0.1.2 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint
    npm info install peakle@0.0.1 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint
    npm info install minimatch@0.2.11 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint
    npm info install esprima@1.1.0-dev into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint
    npm info installOne cli@0.4.3
    npm info installOne underscore@1.4.4
    npm info installOne shelljs@0.1.2
    npm info installOne peakle@0.0.1
    npm info installOne minimatch@0.2.11
    npm info installOne esprima@1.1.0-dev
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/underscore unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/shelljs unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/peakle unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/minimatch unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/esprima unbuild
    npm info preinstall peakle@0.0.1
    npm info preinstall cli@0.4.3
    npm info preinstall minimatch@0.2.11
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/peakle
    npm info linkStuff peakle@0.0.1
    npm info install peakle@0.0.1
    npm info postinstall peakle@0.0.1
    npm info trying registry request attempt 1 at 07:01:42
    npm http GET https://registry.npmjs.org/glob
    npm info trying registry request attempt 1 at 07:01:42
    npm http GET https://registry.npmjs.org/lru-cache
    npm info trying registry request attempt 1 at 07:01:42
    npm http GET https://registry.npmjs.org/sigmund
    npm info preinstall underscore@1.4.4
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/underscore
    npm info linkStuff underscore@1.4.4
    npm info install underscore@1.4.4
    npm info postinstall underscore@1.4.4
    npm info preinstall shelljs@0.1.2
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/shelljs
    npm info linkStuff shelljs@0.1.2
    npm info install shelljs@0.1.2
    npm info postinstall shelljs@0.1.2
    npm info preinstall esprima@1.1.0-dev
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/esprima
    npm info linkStuff esprima@1.1.0-dev
    npm info install esprima@1.1.0-dev
    npm info postinstall esprima@1.1.0-dev
    npm http 304 https://registry.npmjs.org/lru-cache
    npm http 304 https://registry.npmjs.org/glob
    npm info install glob@3.1.21 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli
    npm info installOne glob@3.1.21
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli/node_modules/glob unbuild
    npm http 304 https://registry.npmjs.org/sigmund
    npm info install lru-cache@2.2.2 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/minimatch
    npm info install sigmund@1.0.0 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/minimatch
    npm info installOne lru-cache@2.2.2
    npm info installOne sigmund@1.0.0
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/minimatch/node_modules/lru-cache unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/minimatch/node_modules/sigmund unbuild
    npm info preinstall sigmund@1.0.0
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/minimatch/node_modules/sigmund
    npm info linkStuff sigmund@1.0.0
    npm info install sigmund@1.0.0
    npm info postinstall sigmund@1.0.0
    npm info preinstall lru-cache@2.2.2
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/minimatch/node_modules/lru-cache
    npm info linkStuff lru-cache@2.2.2
    npm info install lru-cache@2.2.2
    npm info postinstall lru-cache@2.2.2
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/minimatch
    npm info linkStuff minimatch@0.2.11
    npm info install minimatch@0.2.11
    npm info postinstall minimatch@0.2.11
    npm info preinstall glob@3.1.21
    npm info trying registry request attempt 1 at 07:01:43
    npm http GET https://registry.npmjs.org/graceful-fs
    npm info trying registry request attempt 1 at 07:01:43
    npm http GET https://registry.npmjs.org/inherits
    npm http 304 https://registry.npmjs.org/inherits
    npm http 304 https://registry.npmjs.org/graceful-fs
    npm info install inherits@1.0.0 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli/node_modules/glob
    npm info install graceful-fs@1.2.0 into /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli/node_modules/glob
    npm info installOne inherits@1.0.0
    npm info installOne graceful-fs@1.2.0
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli/node_modules/glob/node_modules/inherits unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli/node_modules/glob/node_modules/graceful-fs unbuild
    npm info preinstall inherits@1.0.0
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli/node_modules/glob/node_modules/inherits
    npm info linkStuff inherits@1.0.0
    npm info install inherits@1.0.0
    npm info postinstall inherits@1.0.0
    npm info preinstall graceful-fs@1.2.0
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli/node_modules/glob/node_modules/graceful-fs
    npm info linkStuff graceful-fs@1.2.0
    npm info install graceful-fs@1.2.0
    npm info postinstall graceful-fs@1.2.0
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli/node_modules/glob
    npm info linkStuff glob@3.1.21
    npm info install glob@3.1.21
    npm info postinstall glob@3.1.21
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint/node_modules/cli
    npm info linkStuff cli@0.4.3
    npm info install cli@0.4.3
    npm info postinstall cli@0.4.3
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint/node_modules/jshint
    npm info linkStuff jshint@1.0.0
    npm info install jshint@1.0.0
    npm info postinstall jshint@1.0.0
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt-contrib-jshint
    npm info linkStuff grunt-contrib-jshint@0.2.0
    npm info install grunt-contrib-jshint@0.2.0
    npm info postinstall grunt-contrib-jshint@0.2.0
    npm info trying registry request attempt 1 at 07:01:44
    npm http GET https://registry.npmjs.org/grunt
    npm http 304 https://registry.npmjs.org/grunt
    npm info install grunt@0.4.1 into /Users/george/code/npm-3241-testcase
    npm info installOne grunt@0.4.1
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt unbuild
    npm info preinstall grunt@0.4.1
    npm info trying registry request attempt 1 at 07:01:45
    npm http GET https://registry.npmjs.org/colors
    npm info trying registry request attempt 1 at 07:01:45
    npm http GET https://registry.npmjs.org/dateformat/1.0.2-1.2.3
    npm info trying registry request attempt 1 at 07:01:45
    npm http GET https://registry.npmjs.org/eventemitter2
    npm info trying registry request attempt 1 at 07:01:45
    npm http GET https://registry.npmjs.org/findup-sync
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/hooker
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/iconv-lite
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/minimatch
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/nopt
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/rimraf
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/lodash
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/underscore.string
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/which
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/js-yaml
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/async
    npm info trying registry request attempt 1 at 07:01:46
    npm http GET https://registry.npmjs.org/coffee-script
    npm http 304 https://registry.npmjs.org/dateformat/1.0.2-1.2.3
    npm http 304 https://registry.npmjs.org/eventemitter2
    npm http 304 https://registry.npmjs.org/colors
    npm http 304 https://registry.npmjs.org/findup-sync
    npm http 304 https://registry.npmjs.org/hooker
    npm http 304 https://registry.npmjs.org/iconv-lite
    npm http 304 https://registry.npmjs.org/minimatch
    npm http 304 https://registry.npmjs.org/nopt
    npm http 304 https://registry.npmjs.org/rimraf
    npm http 304 https://registry.npmjs.org/lodash
    npm http 304 https://registry.npmjs.org/underscore.string
    npm http 304 https://registry.npmjs.org/which
    npm http 304 https://registry.npmjs.org/js-yaml
    npm http 304 https://registry.npmjs.org/async
    npm http 304 https://registry.npmjs.org/coffee-script
    npm info install glob@3.1.21 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install dateformat@1.0.2-1.2.3 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install eventemitter2@0.4.11 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install colors@0.6.0-1 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install findup-sync@0.1.2 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install hooker@0.2.3 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install iconv-lite@0.2.7 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install minimatch@0.2.11 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install nopt@1.0.10 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install rimraf@2.0.3 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install lodash@0.9.2 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install underscore.string@2.2.0rc into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install which@1.0.5 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install js-yaml@2.0.3 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install async@0.1.22 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info install coffee-script@1.3.3 into /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info installOne glob@3.1.21
    npm info installOne dateformat@1.0.2-1.2.3
    npm info installOne eventemitter2@0.4.11
    npm info installOne colors@0.6.0-1
    npm info installOne findup-sync@0.1.2
    npm info installOne hooker@0.2.3
    npm info installOne iconv-lite@0.2.7
    npm info installOne minimatch@0.2.11
    npm info installOne nopt@1.0.10
    npm info installOne rimraf@2.0.3
    npm info installOne lodash@0.9.2
    npm info installOne underscore.string@2.2.0rc
    npm info installOne which@1.0.5
    npm info installOne js-yaml@2.0.3
    npm info installOne async@0.1.22
    npm info installOne coffee-script@1.3.3
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/glob unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/dateformat unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/eventemitter2 unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/colors unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/findup-sync unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/hooker unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/iconv-lite unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/minimatch unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/nopt unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/rimraf unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/lodash unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/underscore.string unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/which unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/async unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/coffee-script unbuild
    npm info preinstall which@1.0.5
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/which
    npm info linkStuff which@1.0.5
    npm info preinstall dateformat@1.0.2-1.2.3
    npm info install which@1.0.5
    npm info postinstall which@1.0.5
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/dateformat
    npm info linkStuff dateformat@1.0.2-1.2.3
    npm info install dateformat@1.0.2-1.2.3
    npm info postinstall dateformat@1.0.2-1.2.3
    npm info preinstall colors@0.6.0-1
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/colors
    npm info linkStuff colors@0.6.0-1
    npm info install colors@0.6.0-1
    npm info preinstall rimraf@2.0.3
    npm info postinstall colors@0.6.0-1
    npm info preinstall nopt@1.0.10
    npm info preinstall findup-sync@0.1.2
    npm info install graceful-fs@1.1.14 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/rimraf
    npm info installOne graceful-fs@1.1.14
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/rimraf/node_modules/graceful-fs unbuild
    npm info trying registry request attempt 1 at 07:01:47
    npm http GET https://registry.npmjs.org/abbrev
    npm info install lodash@1.0.1 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/findup-sync
    npm info installOne lodash@1.0.1
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/findup-sync/node_modules/lodash unbuild
    npm info preinstall hooker@0.2.3
    npm info preinstall async@0.1.22
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/hooker
    npm info linkStuff hooker@0.2.3
    npm info install hooker@0.2.3
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/async
    npm info linkStuff async@0.1.22
    npm info postinstall hooker@0.2.3
    npm info install async@0.1.22
    npm info postinstall async@0.1.22
    npm info preinstall minimatch@0.2.11
    npm info install lru-cache@2.2.2 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/minimatch
    npm info install sigmund@1.0.0 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/minimatch
    npm info installOne lru-cache@2.2.2
    npm info installOne sigmund@1.0.0
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/minimatch/node_modules/lru-cache unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/minimatch/node_modules/sigmund unbuild
    npm info preinstall graceful-fs@1.1.14
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/rimraf/node_modules/graceful-fs
    npm info linkStuff graceful-fs@1.1.14
    npm info install graceful-fs@1.1.14
    npm info postinstall graceful-fs@1.1.14
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/rimraf
    npm info linkStuff rimraf@2.0.3
    npm info install rimraf@2.0.3
    npm info postinstall rimraf@2.0.3
    npm info preinstall glob@3.1.21
    npm info preinstall sigmund@1.0.0
    npm info install graceful-fs@1.2.0 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/glob
    npm info install inherits@1.0.0 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/glob
    npm info installOne graceful-fs@1.2.0
    npm info installOne inherits@1.0.0
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/glob/node_modules/graceful-fs unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/glob/node_modules/inherits unbuild
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/minimatch/node_modules/sigmund
    npm info linkStuff sigmund@1.0.0
    npm info install sigmund@1.0.0
    npm info postinstall sigmund@1.0.0
    npm info preinstall eventemitter2@0.4.11
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/eventemitter2
    npm info linkStuff eventemitter2@0.4.11
    npm info install eventemitter2@0.4.11
    npm info postinstall eventemitter2@0.4.11
    npm info preinstall lru-cache@2.2.2
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/minimatch/node_modules/lru-cache
    npm info linkStuff lru-cache@2.2.2
    npm info install lru-cache@2.2.2
    npm info postinstall lru-cache@2.2.2
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/minimatch
    npm info linkStuff minimatch@0.2.11
    npm info install minimatch@0.2.11
    npm info postinstall minimatch@0.2.11
    npm info preinstall inherits@1.0.0
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/glob/node_modules/inherits
    npm info linkStuff inherits@1.0.0
    npm info install inherits@1.0.0
    npm info postinstall inherits@1.0.0
    npm info preinstall graceful-fs@1.2.0
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/glob/node_modules/graceful-fs
    npm info linkStuff graceful-fs@1.2.0
    npm info install graceful-fs@1.2.0
    npm info postinstall graceful-fs@1.2.0
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/glob
    npm info linkStuff glob@3.1.21
    npm info install glob@3.1.21
    npm info postinstall glob@3.1.21
    npm info preinstall coffee-script@1.3.3
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/coffee-script
    npm info linkStuff coffee-script@1.3.3
    npm info install coffee-script@1.3.3
    npm info postinstall coffee-script@1.3.3
    npm info preinstall iconv-lite@0.2.7
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/iconv-lite
    npm info linkStuff iconv-lite@0.2.7
    npm info install iconv-lite@0.2.7
    npm info postinstall iconv-lite@0.2.7
    npm info preinstall underscore.string@2.2.0rc
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/underscore.string
    npm info linkStuff underscore.string@2.2.0rc
    npm info install underscore.string@2.2.0rc
    npm info postinstall underscore.string@2.2.0rc
    npm http 304 https://registry.npmjs.org/abbrev
    npm info install abbrev@1.0.4 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/nopt
    npm info installOne abbrev@1.0.4
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/nopt/node_modules/abbrev unbuild
    npm info preinstall abbrev@1.0.4
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/nopt/node_modules/abbrev
    npm info linkStuff abbrev@1.0.4
    npm info install abbrev@1.0.4
    npm info postinstall abbrev@1.0.4
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/nopt
    npm info linkStuff nopt@1.0.10
    npm info install nopt@1.0.10
    npm info postinstall nopt@1.0.10
    npm info preinstall lodash@0.9.2
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/lodash
    npm info linkStuff lodash@0.9.2
    npm info install lodash@0.9.2
    npm info postinstall lodash@0.9.2
    npm info preinstall js-yaml@2.0.3
    npm info trying registry request attempt 1 at 07:01:49
    npm http GET https://registry.npmjs.org/argparse
    npm info preinstall lodash@1.0.1
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/findup-sync/node_modules/lodash
    npm info linkStuff lodash@1.0.1
    npm info install lodash@1.0.1
    npm info postinstall lodash@1.0.1
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/findup-sync
    npm info linkStuff findup-sync@0.1.2
    npm info install findup-sync@0.1.2
    npm info postinstall findup-sync@0.1.2
    npm http 304 https://registry.npmjs.org/argparse
    npm info install argparse@0.1.12 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml
    npm info installOne argparse@0.1.12
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml/node_modules/argparse unbuild
    npm info preinstall argparse@0.1.12
    npm info trying registry request attempt 1 at 07:01:50
    npm http GET https://registry.npmjs.org/underscore
    npm http 304 https://registry.npmjs.org/underscore
    npm info install underscore.string@2.3.1 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml/node_modules/argparse
    npm info install underscore@1.4.4 into /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml/node_modules/argparse
    npm info installOne underscore.string@2.3.1
    npm info installOne underscore@1.4.4
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml/node_modules/argparse/node_modules/underscore.string unbuild
    npm info /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml/node_modules/argparse/node_modules/underscore unbuild
    npm info preinstall underscore@1.4.4
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml/node_modules/argparse/node_modules/underscore
    npm info linkStuff underscore@1.4.4
    npm info install underscore@1.4.4
    npm info postinstall underscore@1.4.4
    npm info preinstall underscore.string@2.3.1
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml/node_modules/argparse/node_modules/underscore.string
    npm info linkStuff underscore.string@2.3.1
    npm info install underscore.string@2.3.1
    npm info postinstall underscore.string@2.3.1
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml/node_modules/argparse
    npm info linkStuff argparse@0.1.12
    npm info install argparse@0.1.12
    npm info postinstall argparse@0.1.12
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt/node_modules/js-yaml
    npm info linkStuff js-yaml@2.0.3
    npm info install js-yaml@2.0.3
    npm info postinstall js-yaml@2.0.3
    npm info build /Users/george/code/npm-3241-testcase/node_modules/grunt
    npm info linkStuff grunt@0.4.1
    npm info install grunt@0.4.1
    npm info postinstall grunt@0.4.1
    npm info build /Users/george/code/npm-3241-testcase
    npm info linkStuff npm-3241-testcase@0.0.0
    npm info install npm-3241-testcase@0.0.0
    npm info postinstall npm-3241-testcase@0.0.0
    npm info prepublish npm-3241-testcase@0.0.0
    grunt@0.4.1 node_modules/grunt
    ├── which@1.0.5
    ├── dateformat@1.0.2-1.2.3
    ├── colors@0.6.0-1
    ├── hooker@0.2.3
    ├── async@0.1.22
    ├── rimraf@2.0.3 (graceful-fs@1.1.14)
    ├── eventemitter2@0.4.11
    ├── minimatch@0.2.11 (sigmund@1.0.0, lru-cache@2.2.2)
    ├── glob@3.1.21 (inherits@1.0.0, graceful-fs@1.2.0)
    ├── coffee-script@1.3.3
    ├── iconv-lite@0.2.7
    ├── underscore.string@2.2.0rc
    ├── nopt@1.0.10 (abbrev@1.0.4)
    ├── lodash@0.9.2
    ├── findup-sync@0.1.2 (lodash@1.0.1)
    └── js-yaml@2.0.3 (argparse@0.1.12)

    grunt-contrib-jshint@0.2.0 node_modules/grunt-contrib-jshint
    └── jshint@1.0.0 (peakle@0.0.1, underscore@1.4.4, shelljs@0.1.2, esprima@1.1.0-dev, minimatch@0.2.11, cli@0.4.3)

