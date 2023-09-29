# escape=`

ARG PARENT_IMAGE
ARG SOLUTION_IMAGE
ARG TOOLS_IMAGE
ARG XTM_CONNECT_IMAGE

FROM ${XTM_CONNECT_IMAGE} as xtm
FROM ${TOOLS_IMAGE} as tools
FROM ${PARENT_IMAGE}

SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]

WORKDIR C:\inetpub\wwwroot

# Copy developer tools and entrypoint
COPY --from=tools C:\tools C:\tools

#Add Xtm Connector
COPY --from=xtm \xtm_assets \inetpub\wwwroot

# Access rights for XtmData folder
RUN icacls 'C:\inetpub\wwwroot\XtmData\*' /grant 'IIS_IUSRS:(F)' /t

