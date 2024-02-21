Sometimes certs are required before any container reaches out to the internet within certain companies.  Example apt, apk, yum, dnf updates

For each Linux distro the location and process can be different.

The 2 certs required are always the same:  COMPANY ROOT.crt and VPN_Root.crt(If VPN is used).  Its best to rename them without spaces and rename the extension from .crt to .pem:
Example:  company_root.pem and zscaler_root.pem

For Alpine put this in your Dockerfile:

#Insert company Certs
COPY certs/* /tmp
RUN cat /tmp/*.pem >> /etc/ssl/certs/ca-certificates.crt

RUN apk --no-cache add ca-certificates \
    && rm -rf /var/cache/apk/*

COPY certs/* /usr/local/share/ca-certificates
RUN update-ca-certificates

For Ubi put this in your Dockerfile:
#Insert company Certs for Ubi
COPY certs/* /etc/pki/ca-trust/source/anchors
RUN update-ca-trust extract

For other distro you'll have to google it.

Some distros may not have update-ca-certificates installed.  For these you will have to put the certs where update-ca-certificates normally puts them in the OS and then do apt install update-ca-certificates and then run update-ca-certificates. 