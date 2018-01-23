21. YT Search Response
    We signed up for the key, now we will start to flash out the results of the serach. We have to fetch the list of videos. video-list.js will get the list of videos also. For now just know that we want that every component will fetch it's own staff, but they all are children of the <App/> so we will fetch data to it and that transfer to the children.
        import YTSearch from 'youtube-api-search';
    We imported our module
        YTSearch({
            key: API_KEY,
            term: 'surfboards
        },
        function(data){
            console.log(data);
        })
    This thing returns us object with videos and all the staff that they have: thumbnails and other info.