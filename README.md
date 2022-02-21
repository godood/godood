jobs:
  dependencies:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Set up Python 3.8
      uses: actions/setup-python@v1
      with:
        python-version: 3.8
    - name: Create BoM Python
      run: |
        pip install cyclonedx-bom
        cyclonedx-py
    - uses: geirem/bom-tracker@master
      env:
        TRACK_TOKEN: ${{ secrets.TRACK_TOKEN }}
        TRACK_INFO_PAGE: https://github.com/geirem/econokindle/security/advisories
        TRACK_HOST: https://track.example.net
