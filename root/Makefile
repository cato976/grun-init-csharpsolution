bootstrapper := paket.bootstrapper.exe
bootstrapperpath := c:/Programs/Git/Paket/.paket/

all: clean test

updatepaket:
	@mkdir -p .paket \
	&& cp $(bootstrapperpath)/$(bootstrapper) .paket/$(bootstrapper) \
	&& .paket/$(bootstrapper) prerelease

install: updatepaket
	.paket/paket.exe install

build:
	c:/Tools/Enterprise/MSBuild/15.0/Bin/MSBuild.exe -nologo -v:q -property:GenerateFullPaths=true

#flags for good development experience with stack trace line number and filenames
test: build
	packages/NUnit.ConsoleRunner/tools/nunit3-console.exe \
	**/bin/**/*Tests.dll \
	-stoponerror \
	-noh \
	-noresult \
	-config=Debug

#clean out bin and obj
clean:
	@find . -type d \( -name "bin" -o -name "obj" \) | xargs rm -rf

.PHONY: install
