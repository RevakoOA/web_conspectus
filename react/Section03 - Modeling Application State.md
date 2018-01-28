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
22. Functional to Class
    We have to refactor our App component from functional to class component.
        const App = () => {
            return(
                <div>
                    <SearchBar />
                </div>
            )
        }
    Will contribute to:
        class App extend Component {
            render() {
                return (
                    <div>
                        <SearchBar />
                    </div>
                );
            }
        }
    List of videos. We want to show  videos when User enters something to the input. So we need state. We will do it in the App component
        constructor(props){
            super(props);

            this.state = { videos: [] };

            YTSearch({ key: API_KEY, term: 'surfboards},
            (videos) => {
                this.setState({ videos })
                // this.setState({ videos: videos}); - the same as above, it's ES6 syntax.
            });
        }
    So now after changing the state we will exactly call the YTSearch and anonymous callback function before rendering. So now we passed our result to the videos. 
    If we will change the name of var data to videos, the same as in the method we can use some ES6 syntax to make it nicer.
23. Props
    