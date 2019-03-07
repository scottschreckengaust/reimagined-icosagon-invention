FROM node:10.15.0
RUN mkdir /usr/src/app
WORKDIR /usr/src/app
ENV NODE_PATH=/node_modules
ENV PATH=$PATH:/node_modules/.bin
ENV PATH=/usr/src/app/node_modules/.bin:$PATH
ENV FORCE_COLOR=true

EXPOSE 3000
EXPOSE 35729

COPY package.json yarn.lock ./

# This is so the container has all the node_modules, not the local directory
RUN yarn install --modules-folder $NODE_PATH

#RUN npm install -g react-scripts@2.1.1

# Copy everything necessary respecting .dockerignore
COPY . ./

# Make yarn the default entry point
ENTRYPOINT ["yarn"]

# Start app by default, although other commands are available as in package.json
CMD ["start"]

# to run "hot" (making local changes) with clearing the console:
# ```bash
# docker run --rm -it -v `pwd`:/usr/src/app -p 3000 -p 35729 --entrypoint="" <image> bash -c "yarn start|cat"
# ```
