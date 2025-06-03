FROM joplin/server:latest

USER node

# Healthcheck usando a porta configurável
HEALTHCHECK --interval=30s --timeout=3s --start-period=40s --retries=3 \
  CMD wget --no-verbose --tries=1 --spider http://localhost:${APP_PORT:-22300}/api/ping || exit 1

# Apenas NODE_ENV fixo para produção
ENV NODE_ENV=production

# Expose com valor padrão
EXPOSE 22300

CMD ["node", "--max-old-space-size=2048", "packages/server/dist/app.js", "start"]