FROM   node:25-alpine3.21
WORKDIR app
COPY . .
RUN npm install && npm run build && npm install -g serve
ENV VITE_API_URL=172.17.0.3
EXPOSE 80
CMD ["serve","-s","dist","-l","80"]
