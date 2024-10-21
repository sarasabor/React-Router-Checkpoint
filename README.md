# React-Router-Checkpoint


Voici comment vous pouvez mettre en œuvre les fonctionnalités demandées dans votre application de films avec React Router :

Modifier l'objet movie : Ajoutez une description et un lien vers la bande-annonce à chaque objet film dans votre état.

javascript
Copier le code
const movies = [
  {
    id: 1,
    title: "Movie Title",
    description: "Movie Description",
    trailerLink: "https://link-to-trailer.com",
  },
  // Ajoutez d'autres films ici...
];
Configurer React Router : Assurez-vous d'installer react-router-dom si ce n'est pas déjà fait.

bash
Copier le code
npm install react-router-dom
Configurer les routes dans App.js :

javascript
Copier le code
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import MovieList from './MovieList';
import MovieDetail from './MovieDetail'; // Composant pour afficher les détails du film

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<MovieList />} />
        <Route path="/movie/:id" element={<MovieDetail />} />
      </Routes>
    </Router>
  );
}

export default App;
Créer MovieList.js pour afficher la liste des films :

javascript
Copier le code
import React from 'react';
import { Link } from 'react-router-dom';

const MovieList = ({ movies }) => {
  return (
    <div>
      {movies.map(movie => (
        <Link key={movie.id} to={`/movie/${movie.id}`}>
          <div className="movie-card">
            <h2>{movie.title}</h2>
            {/* Autres éléments de la carte de film */}
          </div>
        </Link>
      ))}
    </div>
  );
};

export default MovieList;
Créer MovieDetail.js pour afficher les détails du film :

javascript
Copier le code
import React from 'react';
import { useParams, Link } from 'react-router-dom';

const MovieDetail = ({ movies }) => {
  const { id } = useParams();
  const movie = movies.find(movie => movie.id === parseInt(id));

  return (
    <div>
      <h1>{movie.title}</h1>
      <p>{movie.description}</p>
      <a href={movie.trailerLink} target="_blank" rel="noopener noreferrer">Voir la bande-annonce</a>
      <br />
      <Link to="/">Retour à l'accueil</Link>
    </div>
  );
};

export default MovieDetail;
Cela vous permettra de naviguer vers une page de détails pour chaque film, où vous pouvez voir la description et le lien vers la bande-annonce, et également revenir à la page d'accueil.
