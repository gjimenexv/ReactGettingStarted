const CardList = (props) => (
  <div>
      {props.profiles.map(profile => <Card key={profile.id}{...profile}/>)}
  </div>
);

class Card extends React.Component {
	render() {
    const profile = this.props;
  	return (
    	<div className="github-profile">
    	  <img src={profile.avatar_url} />
        <div className="info">
          <div className="name">{profile.name}</div>
          <div className="company">{profile.company}</div>
        </div>
    	</div>
    );
  }
}

class From extends React.Component{
  state = { userName: ''};
  handleSubmit = async (event) =>{
    event.preventDefault();
    const resp = await axios.get(`https://api.github.com/users/${this.state.userName}`);
    this.props.onSubmit(resp.data);
    this.setSate({ userName: ''});
  };
  render(){
    return (
    <form onSubmit={this.handleSubmit}>
        <input type="text" 
          value = {this.state.userName}
          onChange={event => this.setState({userName: event.target.value})}
          placeholder="GitHub Username" 
          required/>
        <button>Add Card</button>
    </form>
    
    );
  }
}

class App extends React.Component {
  state = {profiles: [],};
  
  addNewProfile = (profileData) => {
    this.setState(prevState => ({
      profiles: [...prevState.profiles, profileData],
    }))
  };
	render() {
  	return (
    	<div>
    	  <div className="header">{this.props.title}</div>
        <From onSubmit={this.addNewProfile}/>
        <CardList profiles={this.state.profiles}/>
    	</div>
    );
  }	
}

ReactDOM.render(
	<App title="The GitHub Cards App" />,
  mountNode,
);
