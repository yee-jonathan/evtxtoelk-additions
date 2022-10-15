# EvtxtoElk-Additions

A variation of Dan Gunther's evtxtoelk python script

- Added the ability to parse indvidual evtx files or select a directory for bulk processing.
- Added extension checking for `.evtx` files
- Added usage instructions to README
- Fixed default elk IP so that script will still process without having to give IP and port
- Removed deprecated `_type:` field from parsing

## Installation
1. Clone this repo
2. Create a virtual environment (optional but recommended) \
`python3 -m venv .venv`
3. Install requirements \
`pip install -r requirements.txt`

## Flags
`-dir` specifies path to directory holding evtx files. Cannot be used concurrently with `-file` \
`-file` specifies a single file for parsing. Cannot be used concurrently with `-dir` \
`-i` specifies elasticsearch index to export to. The default index is `hostlogs` \
`-s` specifies size of queue \
`-meta` adds custom metadata if desired

## Usage Examples

Parsing a single evtx file and export to local elasticsearch with default index \
`python3 evtxtoelk.py -file /path/to/file.evtx` or `python3 evtxtoelk.py -file /path/to/file.evtx http://localhost:9200` 

Parsing a directory filled with evtx files and exporting to remote elasticsearch with custom index name \
`python3 evtxtoelk.py -dir /path/to/directory/of/evtx/files -i custom_index http://someremotehost:9200` 