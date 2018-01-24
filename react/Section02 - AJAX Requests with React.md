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
    Let's go to the video-list.js component. It will desn't re-render the state. So it's typical functional component. Let's code it:
        import React from 'react';

        const VideoList = () => {
            return(
                <ul className="col-md-4 list-group">

                </ul>
            )
        }

        export default VideoList;
    We inclued Bootstrap in the html so we can use it to style all the stuff. In the index.js we have to import it
        import VideoList from './components/video-list.js';
    We add also it into the render method. App is the parent to the VideoList so we have to pass some data from parent component to the child component. To pass this data we can props.
        <VideoList videos={this.state.videos} />
    Now we have to pass props in our VideoList component to the function that create the component
        const VideoList = (props) => {
            return(
                <ul className="col-md-4 list-group">
                    {props.videos.length} //we will get 5.
                </ul>
            )
        }
    So we have 0 in the begging, but after fetching 200ms we get 5 videos. Difference between functional and class components is that in functional components we can use simple props.data and in class component we have to code: !!! this.props.data
24. Building Lists with Map
    So we get the array in the VideoList.
    We remove length and we have to build a loop. JS for loops are not desired. Instead using map is better. Syntax of map is:
        array.map(function(number) {return number * 2})
    It will returns new array where each item of the array is doubled. As you might imagine using maps is really nice in React. We can return some data in the html tags. We can render and display even lists. Video-list-item.js. Let's code there:
        import React from 'react';

        const VideoListItem = (props) => {
            return <li>Video</li>
        };

        export default VideoListItem;
    Now we return to the VideoList we can say at the top:
        const VideoList = (props) => {
            const videoItems = props.videos.map((video) => {
                return <VideoListItem video={video} />
            });

            return(
                <ul className="col-md-4 list-group">
                    {videoItems}
                </ul>
            )
        }
    React is very intelligible with the arrays of items. We get now Video 5 times. In the console we have a big error. Let's discuss that in the next section.
25. List Item Keys
    So, what the warning we've got? React is really clever. It wants to get the key of the item.
    Some card needs to be updated, but we forgot to say which one. We have to update the information with the ID of the element that we are going to show. So we have to add that key in rendering the VideoListItem component. Each video has an etag which we can use as a key, because it is unique for every video.
        return <VideoListItem key={video.etag} video={video} />
    It should be not a unique, but consistent. Even if we re-render the item still has to get the same id. 
26. Video List Items
    We don't have the idea what actual video is. In VideoListItem we have a props passed in the function. Let's create a const inside:
        const video = props.video; //we get the video that we try to show in the VideoListItem component.
    We do that in ES6 syntax:
        const VideoListItem = ({video}) => {
            return <li>Video</li>
        };
    All it does it says that the argument has a property video, so declare new property video. It's just the ES6 better syntax. 
    Let's debug. And make conole.log(video) in the function. We have objects and there are titles and desctiptions. So, let's diplay that data that we get with a Bootstrap that we implemented in the HTML. But we have to pass our data in it also. So, the code will look something like that:
        const VideoListItem = ({video}) => {
            return (
                <li className="list-group-item">
                    <div className="video-list media">
                        <div className="media-left">
                            <img className="media-object" src={imageUrl} />
                        </div>
                        <div className="media-body">
                            <div className="media-heading">{video.snippet.title}</div>
                        </div>
                    </div>
                </li>
            );
        };
    So now we have 5 videos for our default search Term. That's amazing!!! It shows us top5 videoResults from YouTube. 
27. Detail Component
    Now we have to concentrate our attention more on the details of the video. 
    video-detail.js

        import React from 'react;
        const VideoDetail = ({ video }) => {
            return (
                <div className = "video-detail col-md-8">
                    <div className="embed-responsive embed-responsive-16by9">
                        <iframe className="embed-responsive-item"></iframe>  
                    </div>
                    <div className="details">
                        <div>
                        </div>
                        <div>
                        </div>
                    </div>
                </div>
            );
        };

        export default VideoDetail