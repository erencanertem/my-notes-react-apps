````react
UserResults.jsx


import { useEffect, useState } from "react";
import Spinner from "../layout/Spinner";
import UserItem from "../users/UserItem";
function UserResults() {
  const [users, setUsers] = useState([]); / We use useState hook for show our data
  const [loading, setLoading] = useState(true);

  useEffect(() => { / When we reload our page, fetchUsers will start
    fetchUsers();
  }, []);

  const fetchUsers = async () => { / Here We fetch data from api
    const response = await fetch(`${process.env.REACT_APP_GITHUB_URL}/users`, {
      headers: { // process.env comes from .env files it add below 
        Authorization: `token ${process.env.REACT_APP_GITHUB_TOKEN}`,
      },
    });
    const data = await response.json();

    setUsers(data); / With setUsers our data will show at page.
    setLoading(false); / When data show at page, loading will turn to false and spinner not show anymore.
  };

  if (!loading) { / With that condition if there is no data, then Spinner will show.
    return (
      <div className="grid grid-cols-1 gap-8 xl:grid-col-4 lg:grid-cols-3 md:grid-cols-2">
        {users.map((user) => (
          <UserItem key={user.id} user={user} />
        ))}
      </div>
    );
  } else {
    return <Spinner />;
  }
}

export default UserResults;



````

​	

````react

import spinner from "./assets/spinner.gif"; / We import example spinner here

function Spinner() {
  return (
    <div className="w-100 mt-20">
      <img
        width={180}
        className="text-center mx-auto"
        src={spinner} 
        alt="Loading..."
      />
    </div>
  );
}

export default Spinner;


````

````
.env file


REACT_APP_GITHUB_URL = "https://api.github.com"
REACT_APP_GITHUB_TOKEN = "your token from github"


````

````react
UserItem.jsx


import { Link } from "react-router-dom"; {/ We import this because, we want to redirect to another page when its clicked.
import PropTypes from "prop-types";

function UserItem({ user: { login, avatar_url } }) { / We made destructure here for take different data from our object.(This could be more than 2) 
  return (
    <div className="card shadow-md compact side bg-base-100">
      <div className="flex-row items-center space-x-4 card-body">
        <div>
          <div className="avatar">
            <div className="rounded-full shadow w-14 h-14">
              <img src={avatar_url} alt="Profile" /> {/its user.avatar_url}
            </div>
          </div>
        </div>
        <div>
          <h2 className="card-title">{login}</h2>
          <Link
            className="text-base-content text-opacity-40"
            to={`/users/${login}`}
          >
            Visit Profile
          </Link>
        </div>
      </div>
    </div>
  );
}

UserItem.propTypes = {/User only can be an object
  user: PropTypes.object.isRequired,
};

export default UserItem;



````

![Screenshot_1](https://user-images.githubusercontent.com/66770659/162552892-7277af06-f9fb-4ece-a429-b83da0d4dfaf.png)






Next ==> Set Github Context
